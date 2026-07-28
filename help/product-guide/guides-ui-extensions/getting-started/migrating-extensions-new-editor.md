---
title: 移轉編輯器2.0的擴充功能框架變更
description: 瞭解如何移轉至Editor 2.0的擴充功能框架
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 75954eab3ac1738705fe2a7280973af39b9214df
workflow-type: tm+mt
source-wordcount: '1904'
ht-degree: 0%

---


# 將擴充功能框架移轉至Editor 2.0 （新編輯器）

本指南可協助擴充功能作者瞭解在AEM Guides中將其自訂功能從&#x200B;**舊編輯器**&#x200B;移至&#x200B;**新編輯器**&#x200B;的相關內容，以便他們能夠以最少的干擾順利規劃轉換。

>[!IMPORTANT]
> 
> 如果您有現有的AEM Guides擴充功能（舊編輯器），包括自訂內容功能表專案、工具列按鈕、對話方塊、屬性或中繼資料邏輯，或內容樣式，本指南可協助您繼續使用新編輯器。

## 概觀

- **您的註冊不會變更**：繼續使用`window.extension` / `tcx.extension.register`。
- **編輯器畫布是新的表面。**內容功能表專案必須宣告新的Widget ID
  `markup_editor_menu`；編輯器中的行為必須停止接觸DOM。
- **停止讀取/寫入DOM**：將`tcx.curEditor.*` DOM存取取代為
  `guides.editor` API： [使用`runUtil(...)`](#migrate-reads-dom-runutil)讀取、[使用`runCommand(...)`](#migrate-writes-dom-mutation-runcommand)寫入、[樣式使用裝飾](#migrate-rendering-only-logic-dom-paint-decorations)以及[透過應用程式事件執行全域動作（儲存）](#migrate-global-actions-savefocus-app-events) 。
- **應用程式殼層功能表（儲存庫、對應檢視器、檔案/資料夾）未變更**：它們仍在執行
舊版框架。
- **兩個編輯器並存**：以陣列同時鎖定兩個編輯器。 當無條件載入&#x200B;**登入**&#x200B;外掛程式時；閘道僅由`guides.editor.version`執行&#x200B;*執行階段*&#x200B;動作（在檔案開啟前會保留`1.0.0`），請檢視[安全地偵測編輯器和啟動程式](#detect-the-Editor-and-bootstrap-safely)。


## 為何變更？

| 條件 | 舊版CKEditor | 新增MarkupEditor |
|---|---|---|
| Source真相 | DOM | ProseMirror檔案 |
| 選擇 | 根檔案上的`getSelection()` | ProseMirror選取（位置/範圍） |
| 若要變更內容 | 變異DOM屬性/類別 | 分派命令（交易） |
| 轉譯 | DOM是永久性的 | DOM是影子DOM中的短暫轉譯，隨時都會重建 |
| 樣式 | Page或clientlib CSS | CSS會透過暫存器外掛程式插入陰影DOM。 請參考[Hello world：僅CSS反白顯示外掛程式](#hello-world-a-css-only-highlight-plugin)，以使用現有類別並新增CSS，以及[移轉僅轉譯邏輯](#migrate-rendering-only-logic-dom-paint-decorations)，以新增類別並新增樣式。 |

任何改變DOM或任何DOM變更的擴充功能都不會保留，而是在下次重新轉譯時遭到淘汰。 移轉基本上是&#x200B;*從DOM-first移至model-first*。

## 安全地偵測編輯器和啟動程式

全域`guides`物件是所有新整合的進入點：

```js
guides.editor    // editor interaction APIs
guides.util      // bundled utility libs (lodash, async)
guides.ready(cb) // fires once at app load (view system ready) — before any file is open
```

`guides.editor.version`報告&#x200B;**目前開啟的編輯器**，因此它只有一次意義
檔案實際上已開啟：

| `guides.editor.version` | 含義 |
|---|---|
| `2.0.0` | MarkupEditor (ProseMirror)檔案已開啟 |
| `1.0.0` | 舊版CKEditor檔案已開啟或尚未開啟任何檔案 |

>[!IMPORTANT]
>
> 發生`guides.ready`事件時，尚未開啟任何檔案，因此不論是否已啟用MarkupEditor，`version`都會報告為`1.0.0`。 請勿使用`version`來判斷外掛程式是否獲得&#x200B;*已註冊* （檢視[外掛程式註冊和執行階段閘道](#plugin-registration-and-runtime-gating)）。 僅將其用於分支&#x200B;*執行階段*&#x200B;行為，並在執行點（例如，在功能表處理常式中）評估它，在此處，檔案一定是開啟的。

### 外掛程式註冊和執行階段閘道

- **註冊** （`registerPlugin`，一次性設定）：在`guides.ready`中無條件執行&#x200B;****。 在舊版編輯器上，這是無害的無操作式：舊版編輯器從不讀取外掛程式登入，而且您的工廠只會在實際建構MarkupEditor時執行。 它&#x200B;**不**&#x200B;擲回。

- **執行階段呼叫** (`runCommand`， `runUtil`， `addDecoration`， ...)：Gate by version存在，且呼叫時不等於「1.0.0」。 它們不會擲回舊版編輯器（它們安全地傳回`false`/`undefined`），但閘道會避免無操作警告，並讓您保留舊版遞補。

```js
guides.ready(() => {
  // Always register — inert on legacy, applied only when a MarkupEditor opens.
  guides.editor.registerPlugin(createMyPlugin);
});

function onMenuClick() {
  if (guides.editor.version && guides.editor.version !== "1.0.0") {
    guides.editor.runCommand('surroundWithElement', 'sup'); // MarkupEditor path
  } else {
    // legacy path (or no-op)
  }
}
```

傳遞&#x200B;**factory** `() => ({ plugin, css })` — 至`registerPlugin`，絕對不要建構外掛程式執行個體。 非函式是唯一拒絕的輸入（會擲回兩個編輯器）。 不要快取編輯器執行個體；每次都呼叫`guides.editor.*` fresh。

### Hello world：僅限CSS的醒目提示外掛程式

最小的實用擴充功能只提供&#x200B;**CSS**無操作的ProseMirror外掛程式加上樣式。 這個
反白編輯器內具有黃色背景的每個`<note>`元素：

```js
guides.ready(() => {
  guides.editor.registerPlugin(() => ({
    plugin: new guides.editor.prosemirror.state.Plugin({}), // no behavior — CSS only
    css: `[data-xml-element="note"] { background: #fff3cd; outline: 1px solid #ffe08a; }`
  }));
});
```

- 每個元素都會呈現為`data-xml-element="<tag>"`，因此您可以以此方式鎖定任何DITA元素
(`note`， `codeblock`， `section`， `table`， ...)。
- CSS **必須**透過registerPlugin出貨：編輯器位於影子DOM中，因此page/clientlib CSS無法
觸及。
- 開啟包含`<note>`的DITA主題以檢視其套用。 註冊為無條件(§2.1)，
因此即使`version`在`guides.ready`時間仍為`1.0.0`，這是安全的。


## 清查您的擴充功能（grep檢查清單）

```bash
# DOM-first reads that will break
grep -rnE "rootDocument|rootElement|getSelection\(|selectedHtml|selectedText|\.xmlDoc|\.ancestors\b" src

# DOM/legacy writes that will break
grep -rnE "updateAttributes\(|setAttribute\(|classList\.|\.saveFile\(|resetDirty\(|validateRangeForInsertion\(" src

# The editor handle itself
grep -rn "tcx.curEditor" src

# Context-menu targeting + page CSS
grep -rnE "contextMenuWidget|dita_editor_menu|author_outline_element" src
grep -rn "dita_content_overrides" .
```

每次點選都是移轉專案。 將每個分類為： *內容功能表介面*、*狀態讀取*、*內容
寫入*、*全域動作*、*僅轉譯*&#x200B;或&#x200B;*CSS*。


## 兩個編輯器通用

以下行為和結構同樣適用於兩個編輯器：

- **註冊：** `window.extension[id] = config`和/或`tcx.extension.register(id, config)`日期
`tcx-loaded`事件。
- **設定物件形狀：** `{ id, contextMenuWidget, view: { items }, controller }`。
- **應用程式殼層內容功能表**&#x200B;會保留其現有的Widget ID和舊版行為：

  | 表面 | Widget id （未變更） |
  |---|---|
  | 存放庫面板（檔案/資料夾） | `repository_panel` / `file_options` / `folder_options` |
  | 地圖檢視器 | `ditamap_viewer` / `map_view_options` |
  | 基線/預設面板 | `baseline_panel_menu` / `preset_item_menu` |

  以這些表面為目標的專案需要&#x200B;**新編輯器的無變更**，請勿將其移至
  `markup_editor_menu`.

## API取代參考

| 舊版(`tcx.curEditor…` / DOM) | 新增MarkupEditor |
|---|---|
| `tcx.curEditor.filePath` | `guides.editor.filePath` |
| `getSelection()` / `selectedHtml` / `selectedText` | `runUtil('getSelectedXml' / 'getSelectedPlainText' / 'hasSelection')` |
| `rootDocument.querySelector(tag)` | `runUtil('findPositionRange' / 'findPositionRanges', tag)` |
| 專案`.getAttribute` / `xmlDoc.attributes` | `runUtil('getAttributeAtPosition', pos, name)` / `getSerializableAttributes(xpath)` |
| 根識別碼(`querySelector('[concept]').id`) | `runUtil('getAttributeAtPosition', 0, 'id')` |
| `editor.ancestors` | `runUtil('getAncestorsDetails' / 'getAncestorXpaths')` |
| `editor.updateAttributes(attrs, root)` | `runCommand('setNodeXmlAttributes', 0, attrs)` |
| 在元素上設定attr | `runCommand('setNodeXmlAttribute', pos, name, value)` |
| 換行/插入/取消換行 | `runCommand('surroundWithElement' / 'insertXml' / 'unwrapNode', …)` |
| `canInsertXmlElement` / `validateRangeForInsertion` | `canRunCommand(name, …)` / `canInsertXmlElement(tag)` |
| `editor.focus()` | `guides.editor.focus()` |
| `tcx.curEditor.saveFile()` | `tcx.eventHandler.next(KEYS.AUTHOR_SAVE_KEY)` |
| 樣式的`setAttribute` / `classList` | `addDecoration` / `batchDecorations` / `registerPlugin` |
| 編輯器內容的page/clientlib CSS | `registerPlugin({ css })` （陰影DOM） |
| `contextMenuWidget: 'dita_editor_menu'` | `['dita_editor_menu', 'markup_editor_menu']` |


## 移轉內容功能表專案（編輯器畫布）

這僅適用於以&#x200B;**編輯器** (`dita_editor_menu`，
`author_outline_element`)，即編輯介面內的滑鼠右鍵/階層連結功能表。

### 如何在新的編輯器中路由

```
window.extension[id]  ─►  filtered by contextMenuWidget == 'markup_editor_menu'
                      ─►  view.items rendered in the canvas menu
   (click) ───────────►  fires an extension event:
                          • eventid is a known global key  → run as a built-in editor command
                          • otherwise                       → your controller[eventid]() runs
```

### 新增新的Widget ID （陣列可讓舊版繼續運作）

```js
// BEFORE
contextMenuWidget: 'dita_editor_menu',
// AFTER
contextMenuWidget: ['dita_editor_menu', 'markup_editor_menu'],
```

### 保持預期的形狀

- 可操作專案在`view.items`下具有`data.eventid`。
- 每個`controller`方法名稱&#x200B;**與**&#x200B;其`eventid`完全相符。

```js
view: {
  items: [{
    displayName: 'Edit Cross Reference',
    icon: 'link',
    data: { eventid: 'editCrossReference' },
    target: { key: 'displayName', value: 'Cut', viewState: 'prepend' }
  }]
},
controller: {
  editCrossReference() { /* runs on click */ }
}
```

### 重新錨點`target`

新功能表會針對MarkupEditor自己的功能表專案解析`target`。

- `target.key`: `displayName | id | icon | eventid`
- `target.viewState`: `append | prepend | replace`
- 錨點為穩定的原生專案，例如&#x200B;**`Cut`**。
- 如果錨點未解析，專案仍會出現，但會停留在預設位置
（不是錯誤，請修正錨點）。

### 選擇每個料號的製程

```js
data: { eventid: 'AUTHOR_CUT' }          // built-in command → routed natively, no controller needed
data: { eventid: 'editCrossReference' }  // custom → runs controller.editCrossReference()
```

將`readOnly: true`新增至必須持續啟用唯讀內容的專案。

### 重寫處理常式內文

處理常式通常會讀取選取範圍並變異節點，將節點從DOM移轉。

## 移轉讀取(DOM： `runUtil`)

```js
// BEFORE — DOM selection / queries
const { editor } = tcx.curEditor;
const html = editor.selectedHtml;
const topicId = editor.rootDocument.querySelector('[data-tcx-tag="concept"]').id;

// AFTER — read from the document model
const selectedXml = guides.editor.runUtil('getSelectedXml');
const hasSel      = !!guides.editor.runUtil('hasSelection'); // check if selection is empty
const topicId     = guides.editor.runUtil('getAttributeAtPosition', 0, 'id'); // root = position 0
```

依標籤尋找節點、依ID比對、讀取XML屬性：

```js
let value = '';
for (const range of (guides.editor.runUtil('findPositionRanges', 'xref') || [])) {
  const id = guides.editor.runUtil('getAttributeAtPosition', range.from, 'id');
  if (String(id) !== String(targetId)) continue;
  value = guides.editor.runUtil('getAttributeAtPosition', range.from, 'placeholdertext') || '';
  break;
}
```

**讀取公用程式：** `getTextPos`，`getNodePosition`，`getSelectedXml`，`getSelectedPlainText`，
`hasSelection`, `getAncestorsNames`, `getAncestorsDetails`, `getAncestorXpaths`,
`findPositionRange`, `findPositionRanges`, `getAttributeAtPosition`, `getSerializableAttributes`. 請參閱[附錄](#appendix-a-more-exposed-utils-examples)。


## 移轉寫入（DOM突變： `runCommand`）

```js
// BEFORE
const root = editor.rootElement.findOne('[data-tcx-tag="concept"]');
editor.updateAttributes({ docOwner: 'Jane' }, root);

// AFTER — update the model; persists across rerenders
guides.editor.runCommand('setNodeXmlAttributes', 0, { docOwner: 'Jane' });
```

```js
// Set one attribute at a found position
guides.editor.runCommand('setNodeXmlAttribute', pos, 'placeholdertext', text);

// Wrap / insert / unwrap
guides.editor.runCommand('surroundWithElement', 'sup');
guides.editor.runCommand('insertXml', '<sup></sup>', undefined, { setCursorInContent: true });
guides.editor.runCommand('unwrapNode');
```

**必備條件**

```js
guides.editor.focus();
if (!guides.editor.canInsertXmlElement('xref')) {
  return tcx.util.showAlert('warning', 'xref is not allowed here'); 
}
if (guides.editor.canRunCommand('surroundWithElement', 'sup')) {
  guides.editor.runCommand('surroundWithElement', 'sup');
}
```

**命令：** `setNodeXmlAttributes`，`setNodeXmlAttribute`，`surroundWithElement`，`insertXml`，
`unwrapNode`. 請參閱[附錄](#appendix-b-more-exposed-commands-examples)。

## 移轉全域動作（儲存/焦點：應用程式事件）

```js
// BEFORE
tcx.curEditor?.saveFile?.();
// AFTER
tcx.eventHandler.next(tcx.eventHandler.KEYS.AUTHOR_SAVE_KEY);
```

`resetDirty(...)`和`tcx.curEditor.html`沒有MarkupEditor等同專案，請卸除它們；儲存
透過事件集中處理已變更狀態。 使用`guides.editor.focus()`作為焦點。


## 移轉僅限轉譯的邏輯（DOM paint：裝飾）

任何藉由變更DOM而新增CSS類別、`data-*`屬性或「顯示文字」的內容，都必須
成為**裝飾**，或它在重新呈現時消失。 以下是簡單的宣告式案例：

```js
guides.editor.addDecoration('important-sections', 'section', {
  class: 'section-important',
  computeAttributes: (node, ctx) => ({ 'data-number-label': String(ctx.index + 1) }),
  filter: (node) => node.attrs?.xmlAttrs?.importance === 'high'
});

guides.editor.batchDecorations([
  { action: 'remove', id: 'legacy-numbering' },
  { action: 'add', id: 'division-numbering', selector: 'conbody', options: { class: 'division-numbering' } }
]);

guides.editor.removeDecoration('important-sections');
guides.editor.clearDecorations();
guides.editor.getDecorations();
```

複雜案例（自訂狀態、透過交易中繼的中斷狀態、Widget文字）：註冊
ProseMirror外掛程式一次，使用公開的程式庫：

```js
const createXrefPlugin = () => {
  const { Plugin, PluginKey } = guides.editor.prosemirror.state;
  const { Decoration, DecorationSet } = guides.editor.prosemirror.view;
  return {
    plugin: new Plugin({ key: new PluginKey('xrefDisplay'), props: { decorations(state) { /* … */ } } }),
    css: `.xref-broken { text-decoration: underline wavy red; }`
  };
};

guides.ready(() => guides.editor.registerPlugin(createXrefPlugin));
```

在應用程式載入時註冊外掛程式（一次），不會在對話方塊內或重複註冊，登入不會進行重複資料刪除。`registerPlugin`只接受&#x200B;**factory函式**，不接受外掛程式執行個體。
`guides.editor.prosemirror`公開： `state`、`model`、`view`、`transform`、`commands`、`keymap`、
`history`、`tables`、`dropcursor`、`collab`、`markdown`。


## 移轉CSS （頁面clientlib→陰影DOM）

MarkupEditor會在&#x200B;**陰影DOM**&#x200B;內轉譯；頁面層級和AEM clientlib CSS無法存取它。

```js
guides.editor.registerPlugin(() => ({
  plugin: new guides.editor.prosemirror.state.Plugin({}),   // no-op, CSS only
  css: `[data-xml-element="codeblock"] { font-family: monospace; background: #f5f5f5; }`
}));
```

舊版內容clientlib類別(`apps.guides.xml_editor.dita_content_overrides`)仍然
僅設定舊版編輯器的樣式，如果您同時支援這兩個編輯器，請保留它，但知道它在MarkupEditor上已插入。

## 存取即時EditorView （外掛程式`view` prop）： DOM逸出影格

裝飾和指令是首選方法。 不過，有些效果無法實作為裝飾。 在這些情況下，請使用外掛程式`view`屬性來存取即時`EditorView`，並在`editorView.dom`上操作。 這是直接與轉譯編輯器DOM互動的唯一受支援方式。

```js
const createMyPlugin = () => {
  const { Plugin } = guides.editor.prosemirror.state;
  return {
    plugin: new Plugin({
      view(editorView) {
        const root = editorView.dom;          // the shadow-DOM editor node
        const apply = () => { /* re-color / rewrite target nodes in `root` */ };
        apply();
        return {
          update(view, prevState): apply,                       // re-apply after every rerender
          destroy() { /* remove any listeners/observers */ },
        };
      },
    }),
    css: `/* ... */`,
  };
};

guides.ready(() => guides.editor.registerPlugin(createMyPlugin));
```

**護欄**：

- 僅逸出影格，使用類別、標籤和樣式的裝飾。
- `editorView.dom`是唯一支援的控制代碼；
- 從`update()`重新套用，讓變更在轉譯後仍有效；在`destroy()`中清除。

## 外掛程式註冊生命週期

`guides.ready`中的`registerPlugin`只登入工廠一次。 工廠本身會再次執行
每次開啟檔案時 — 開啟的每個MarkupEditor檔案都會重新叫用，以建置該檔案的
外掛程式例項。

## 常見問題

- 其中DOM程式碼會處理節點和`Range`，MarkupEditor會處理&#x200B;**位置**，純整數會索引至檔案（`0` =檔案開始，即根目錄）。 `range`是`{ from, to }`，兩個位置包圍範圍 — 不是DOM `Range`。 位置會隨著檔案變更而移動，因此請勿在編輯時快取位置。
- **專案未出現在新編輯器功能表中**：遺失`contextMenuWidget`
  `markup_editor_menu`，或設定是在&#x200B;*編輯器開啟後*登入（設定已讀取）
  一次於編輯器建構註冊於應用程式載入時)。
- **專案出現在錯誤的位置**： `target`錨點無法解析；錨點會出現在專案
存在於新功能表中（例如`Cut`）。
- **變更「有效」後消失**：您已變更DOM。 使用指令（寫入）或裝飾
（樣式）。
- **CSS沒有效果**：它的頁面層級；編輯器在陰影DOM中。 使用`registerPlugin({ css })`。
- **不安全的衛兵擲回**：類似`if (!tcx.curEditor && !tcx.curEditor.editor)`的模式評估
  `.editor`在假物件上。改為警衛`guides.editor`功能：
  `if (!guides?.editor) return;`.
- **嘗試移轉app-shell功能表**：儲存庫/對應/檔案功能表不是編輯器畫布；
保留其舊版widget id。

## 驗證檢查清單

- 內容功能表專案同時出現在&#x200B;**舊版和MarkupEditor功能表中**。
- 專案落在預期位置。
- 自訂`eventid`執行`controller[eventid]`；全域金鑰引發內建命令。
- 輸入/重新呈現後，狀態讀取會傳回正確的值（模型，而非陳舊的DOM）。
- 內容寫入&#x200B;*在儲存並重新開啟後持續存在*。
- 重新演算後仍保留裝飾。
- Shadow-DOM CSS明顯會套用至編輯器內。
- 透過`AUTHOR_SAVE_KEY`儲存引發並清除已變更的狀態。
- `readOnly`專案在鎖定的內容中行為正確。
- 預覽或並排；有意的唯讀DOM工作會維持原狀。
- `grep -rn "tcx.curEditor" src`是乾淨的（或僅記錄有意餘數）。
- 外掛程式只登入一次，在`guides.ready`內。


## 建議的轉出順序

1. **Bootstrap**：在`guides.ready`中完成安裝程式；無條件註冊外掛程式，並只新增`version`閘道&#x200B;*執行階段*&#x200B;動作（如需詳細資料，請檢視[外掛程式註冊和執行階段閘道](#plugin-registration-and-runtime-gating)）。
2. **內容功能表表面**：新增`markup_editor_menu`，修正`target`錨點。 專案隨即顯示。
3. **讀取**：將選擇/屬性讀取移轉到`runUtil`。
4. **寫入**：移轉變動至`runCommand`；儲存至應用程式事件。
5. **轉譯**：將DOM樣式移至裝飾/ `registerPlugin`；將CSS移至陰影DOM。
6. **強制**：修正不安全的防護裝置、移除編輯器控制代碼、驗證兩個編輯器。

一次移轉一個表面，並保持舊版路徑正常運作（陣列+版本閘道），以便
單一擴充功能組建會在整個轉變中的兩個編輯器中執行。

## 附錄A：更多公開的Util （範例）

透過`runUtil`尋找以下要使用的util。

| 使用率 | 引數→傳回 | 作用 |
|---|---|---|
| `getTextPos` | `(): { start, end }` | 目前選取的文位元組點邊界 |
| `getValidElementNames` | `(ancestorLevel?): ElementName[]` | 可在目前選取範圍合法插入/包裝的元素名稱。 |
| `getValidElementNamesBefore` | `(): ElementName[]` | 元素名稱在目前選取範圍的前面有效。 |
| `getSelectedText` | `(): string` | 原始選取的文字。 |
| `getSerializableAttributes` | `(): { [key]: string }` | 目前節點的XML屬性對應，以屬性名稱作為索引鍵。 |
| `getTagName` | `(): string \| null` | 目前節點的標籤名稱。 |
| `hasSelection` | `(): boolean` | 目前是否選取任何內容。 |
| `isSelectionEditable` | `(): boolean` | 是否可編輯目前的選取範圍。 |
| `getAncestorPos` | `(name): number \| undefined` | 目前選取範圍中具有指定元素名稱的最近上階位置。 |
| `getValidWrapNodeElementNames` | `(): ElementName[]` | 在目前選取專案對`wrapNode`有效的元素名稱。 |
| `getValidRenameNodeElementNames` | `(): ElementName[]` | 元素名稱目前節點可合法重新命名為。 |
| `getValidSurroundElementNames` | `(): ElementName[]` | 在目前選取專案對`surroundWithElement`有效的元素名稱。 |
| `serialize` | `(doc?): string` | 將ProseMirror檔案（或整個檔案）序列化為XML。 |
| `getSelectedXml` | `(range?): string` | 目前選取範圍的XML，或明確的`{ from, to }`範圍。 |
| `getRangeXml` | `(xpaths): string` | 一或多個xpath物件範圍的XML （請參閱§8的xpath注意事項 — 這是物件表單，而不是字串表單）。 |
| `mapToXpath` | `(position, doc?): XPathPosition` | 將位置轉換為物件表單xpath。 |
| `inverseMap` | `(xpath \| position, doc?): number` | 將物件表單xpath （或位置）轉換回位置。 |
| `getAncestorsDetails` | `(): { ancestors, previousSibling, nextSibling, currNode } \| undefined` | 目前節點的上階鏈加上立即同層級。 |
| `getAncestorsNames` | `(): ElementName[]` | 上階鏈只作為目前節點的元素名稱。 |
| `getPreviousSibling` | `(): ElementName \| undefined` | 上一個同層級元素的名稱。 |
| `getNextSibling` | `(): ElementName \| undefined` | 下一個同層級元素的名稱。 |
| `getAncestorXpaths` | `(includeNodeAtPosition?): { tag, xpath }[]` | 上階鏈為`{tag, xpath}`對 — 物件表單xpath，而非`updateAttributeByXpath`字串表單(§8)。 |
| `getSelectedPlainText` | `(range?): string` | 目前選取範圍的純文字或明確的範圍。 |
| `getDecorations` | `(): string[]` | 目前套用之所有裝飾的ID。 |
| `getResolvedDitaDocumentTitle` | `(props?): string` | 已解析DITA檔案的顯示標題。 `props`： `doc`以特定檔案為目標，`allowedPrefixElements`允許標題前置詞元素。 |

## 附錄B：更多公開的命令（範例）

以下命令是透過`guides.editor.runCommand(name, ...args)`公開的其他範例。
如果任何具有`guides.editor.canRunCommand(name, ...args)`的命令可能不適用於目前內容，請先加以保護。

| 命令 | 引數 | 作用 |
|---|---|---|
| `focusEditor` | `()` | 焦點在編輯器上。 |
| `unwrapNode` | `()` | 移除目前選取範圍處的環繞元素，保留其子系。 |
| `surroundWithElement` | `(elementName, attrs?, groupInline?)` | 以新的內嵌/區塊元素來包裝目前選取範圍。 `attrs`：在新包裝專案上設定的XML屬性對應。 |
| `insertXml` | `(xml)` | 在游標處插入XML片段。 |
| `replaceSelectionWithXml` | `(xml)` | 以XML取代目前的選取範圍。 |
| `insertText` | `(text)` | 在游標處插入純文字。 |
| `selectNodesFromXpaths` | `(xpaths)` | 選取指定物件格式xpath的一或多個節點。 |
| `delete` | `()` | 刪除目前的選取專案。 |
| `undo` / `redo` | `()` | 標準還原/重做。 |
| `removeDecoration` | `(id)` | 依ID移除單一裝飾。 |
| `clearDecorations` | `()` | 移除目前開啟檔案中的所有裝飾。 |
| `setFileReadOnly` | `(readOnly: boolean)` | 切換檔案的唯讀模式。 |
| `generateUniqueId` | `()` | 產生並指派唯一ID屬性給目前節點。 |