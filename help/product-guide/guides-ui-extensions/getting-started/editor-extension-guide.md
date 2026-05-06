---
title: 編輯器2.0的擴充功能框架變更
description: 瞭解關於Editor 2.0擴充功能框架的變更
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 3f38264b6ce09366d07cdd302c9c53e8abcf4b7c
workflow-type: tm+mt
source-wordcount: '2003'
ht-degree: 3%

---

# 編輯器2.0 （新編輯器）的擴充功能框架變更

本檔案涵蓋新增到`guides.editor` （和`guides`）的所有API，這些是新編輯器（ProseMirror型編輯器）的擴充功能架構的一部分。 這些API允許外部擴充功能與編輯器互動，而不需要直接DOM操作或內部實作知識。

## 概觀

全域`guides`物件是所有擴充功能整合的進入點：

```js
guides.editor    // Editor interaction APIs
guides.util      // Utility libraries (lodash, async)
guides.ready(cb) // Lifecycle hook fires when the editor is fully loaded
```

所有`guides.editor` API都可以安全地從擴充功能控制器、工具列處理常式及對話方塊邏輯呼叫。

## 生命週期

`guides.ready(callback)`：登入回呼以在頁面檢視管理員完全載入後執行。 在註冊外掛程式或執行任何編輯器設定之前使用此選項。

**簽章：**

```ts
guides.ready(callback: () => void): void
```

**範例：**

```js
guides.ready(() => {
  // Safe to access guides.editor APIs here
  guides.editor.registerPlugin(createMyPlugin);
});
```

## 編輯器狀態屬性

- `guides.editor.filePath`：傳回目前作用中檔案的檔案路徑。

  **型別：** `string | undefined`

  **範例：讀取中繼資料API呼叫的檔案路徑：**

  ```js
  const filePath = guides.editor.filePath;
  if (filePath) {
  tcx.api.getMetadata(filePath).subscribe((metadata) => {
    // use metadata...
    });
  }
  ```

  **範例：以檔案位置為基礎的條件式邏輯**

  ```js
  const filePath = guides.editor.filePath;
  if (filePath?.endsWith(".ditamap")) {
    // ditamap-specific handling
  }
  ```

- `guides.editor.version`：傳回目前載入之編輯器的版本字串。

  | 值 | 編輯器 |
  |---------|------------------------------------|
  | `1.0.0` | 舊版CKEditor (`xml_author_view`) |
  | `2.0.0` | 新編輯器(ProseMirror-based) |

  **型別：** `string`

  **範例：**

  ```js
  if (guides.editor.version  === '1.0.0') {
    // CKEditor specific logic 
  }
  ```

- `guides.editor.appState(keyName)`：依索引鍵名稱從應用程式模型讀取值。

  **簽章：**

  ```ts
  guides.editor.appState(keyName: string): unknown
  ```

  **範例：**

  ```js
  const editorMode = guides.editor.appState('editorMode');
  ```

## 編輯器互動

- `guides.editor.focus()`：將焦點設定為作用中編輯器。 在執行需要編輯器取得焦點的命令之前，請先呼叫此項。

  **簽章：**

  ```ts
  guides.editor.focus(): boolean
  ```

  **範例：插入內容前焦點**

  ```js
  guides.editor.focus();
  const hasSelection = !!guides.editor.runUtil('hasSelection');
  // ...proceed with wrap or insert
  ```

- `guides.editor.canInsertXmlElement(tagName, insertAfter?)`：檢查指定的XML專案是否可插入目前的游標位置。

  **簽章：**

  ```ts
  guides.editor.canInsertXmlElement(tagName: string, insertAfter?: boolean): boolean
  ```

  **範例：插入`<xref>`**&#x200B;前先防範

  ```js
  const canInsert = guides.editor.canInsertXmlElement("xref");
  if (!canInsert) {
    return tcx.util.showAlert("warning", "xref is not allowed here");
  }
  ```

  **範例：插入`<sup>` /`<sub>`**&#x200B;前先防範

  ```js
  const canInsert = guides.editor.canInsertXmlElement("sup");
  if (!canInsert) {
    return tcx.util.showAlert("warning", "superscript is not allowed here");
  }
  ```

- `guides.editor.selectCurrentBlockElement()`：在編輯器中選取目前的區塊層級元素。

  **簽章：**

  ```ts
  guides.editor.selectCurrentBlockElement(): boolean
  ```

  **範例：**

  ```js
  guides.editor.selectCurrentBlockElement();
  ```

- `guides.editor.getValidElementNamesForInsertion(args)`：傳回可以在目前位置插入的有效XML元素名稱清單。

  **簽章：**

  ```ts
  guides.editor.getValidElementNamesForInsertion(args: {
    insertMode?: 'after' | 'before' | 'rename',
    strict: boolean
  }): string[] | false
  ```

  **範例：**

  ```js
  const validElements = guides.editor.getValidElementNamesForInsertion({
    insertMode: 'after',
    strict: true
  });
  ```

- `guides.editor.updateAttributeByXpath(args)`：更新其XPath所識別之節點上的特定XML屬性。 委派給使用中編輯器的`updateAttributeByXpath`方法。

  **簽章：**

  ```ts
  guides.editor.updateAttributeByXpath(args: UpdateXpathArgs): any
  ```

## 命令執行

- `guides.editor.runCommand(commandName, ...args)`：在新編輯器上執行命名的命令。 如果命令成功，則傳回`true`，否則傳回`false`。

  **簽章：**

  ```ts
  guides.editor.runCommand(commandName: string, ...args: any[]): boolean
  ```

  **可用的命令**

  >[!NOTE]
  >
  > 穩定性：下列指令是公用介面的一部分。 它們的名稱、簽章和可觀察的行為會視為穩定並保持相容性。 編輯器中可能會出現其他命令；但是，這些是內部命令，不適用於外部使用，可能會變更或移除，恕不另行通知。

  | 類別 | 命令 | 引數 | 說明 |
  |---|---|---|---|
  | 一般 | `undo` | _（無）_ | 取消上一個檔案變更 |
  | 一般 | `redo` | _（無）_ | 重新執行上次復原的變更 |
  | 選擇 | `select` | `from: number, to?: number` | 選取從`from`到`to`的範圍（如果省略`to`，則只有`from`） |
  | 選擇 | `cursor` | `pos: number` | 將游標移至`pos` |
  | 選擇 | `selectNodesFromXpaths` | `xpaths: Array<{path: Array<{name: string, count: number}>}>` | 選取XPath位置所識別的節點 |
  | 格式化 | `toggleBold` | _（無）_ | 切換目前選取範圍上的粗體格式設定 |
  | 格式化 | `toggleItalic` | _（無）_ | 切換目前選取範圍上的斜體格式 |
  | 格式化 | `toggleUnderline` | _（無）_ | 切換目前選取範圍上的底線格式設定 |
  | 格式化 | `toggleFormatting` | `markType: string, allowEmptySelection?: boolean` | 切換選取專案上的格式元素（例如，`'b'`、`'i'`、`'sup'`、`'sub'`） |
  | 插入 | `insertText` | `text: string` | 在游標處插入純文字 |
  | 插入 | `insertXml` | `xml: string, position?: number, options?: InsertXmlOptions` | 在游標或指定位置插入原始XML |
  | 插入 | `insertXmlAfterElement` | `elementName: string, xmlString: string` | 在符合`elementName`的最近上階後面緊接著插入XML |
  | 插入 | `replaceSelectionWithXml` | `xmlString: string` | 以指定的XML取代目前的選取範圍 |
  | 節點作業 | `surroundWithElement` | `tagName: string, attrs?: Record<string,unknown>, replaceTextWithEmptyNode?: boolean` | 以指定的元素括住目前的選取範圍 |
  | 節點作業 | `wrapNode` | `type: string, target?: number, attrs?: Record<string, unknown>` | 在`type`的元素中包裝`target` （或目前節點）的節點 |
  | 節點作業 | `renameNode` | `newNodeName: string` | 重新命名目前節點的元素 |
  | 節點作業 | `unwrapNode` | _（無）_ | 移除目前節點的包裝函式元素，保留其內容 |
  | 刪除 | `deleteSelection` | _（無）_ | 刪除目前選取的內容 |
  | 刪除 | `deleteNode` | _（無）_ | 刪除整個目前節點 |
  | 屬性 | `setNodeXmlAttributes` | `position: number, attrs: Record<string, unknown>` | 在位於`position`的節點上設定多個XML屬性 |
  | 屬性 | `setNodeXmlAttribute` | `position: number, attrName: string, value: string` | 在位於`position`的節點上設定單一XML屬性 |
  | 清單 | `toggleList` | `listName: 'ol' \| 'ul'` | 在指定型別的清單和段落之間切換目前區塊 |
  | 表格 | `addRowAfter` | `count?: number` | 在目前列下方新增`count`列（預設為1） |
  | 表格 | `addColumnAfter` | `count?: number` | 在目前欄的右側新增`count`欄（預設為1） |
  | 表格 | `deleteRow` | _（無）_ | 刪除目前列 |
  | 表格 | `deleteColumn` | _（無）_ | 刪除目前欄 |
  | 表格 | `mergeCells` | _（無）_ | 合併目前選取的儲存格 |
  | 剪貼簿 | `copy` | _（無）_ | 將目前選取內容複製到剪貼簿 |
  | 剪貼簿 | `cut` | _（無）_ | 將目前的選取範圍剪下到剪貼簿 |
  | 尋找和取代 | `setSearchQuery` | `query: string, options?: { caseSensitive?: boolean, regex?: boolean }` | 設定使用中的搜尋查詢 |
  | 尋找和取代 | `findNext` | _（無）_ | 移至下一個搜尋相符專案 |
  | 尋找和取代 | `replaceAll` | `replacement?: string` | 以`replacement`取代目前搜尋查詢的所有相符專案 |

   - **範例：在節點**&#x200B;上設定多個屬性

     ```js
     guides.editor.runCommand(
       "setNodeXmlAttributes",
       rootRange.from,
       { createdDate: "2024-01-01", author: "Jane Doe" }
     );
     ```

   - **範例：在節點**&#x200B;上設定單一屬性

     ```js
     guides.editor.runCommand(
       "setNodeXmlAttribute",
       range.from,
       "placeholdertext",
       "Chapter 3 — Safety Requirements"
     );
     ```

   - **範例：使用元素將選取範圍換行，並設定屬性**

     ```js
     const didWrap = guides.editor.runCommand(
       "surroundWithElement",
       "ph",
       { outputclass: "highlight" },
       true   // replace text content with empty node
     );
     ```

   - **範例：在`<sup>`中自動換行（切換上標）**

     ```js
     const didWrap = guides.editor.runCommand('surroundWithElement', 'sup');
     if (!didWrap) {
       tcx.util.showAlert("warning", "superscript is not allowed here");
     }
     ```

   - **範例：解除目前節點的包裝（關閉上標）**

     ```js
     const didUnwrap = guides.editor.runCommand('unwrapNode');
     ```

   - **範例：在游標處插入XML，插入插入號置於**&#x200B;內

     ```js
     guides.editor.runCommand(
       'insertXml',
       '<sup></sup>',
       undefined,
       { setCursorInContent: true, focusEditor: true, selectInsertedXml: false }
     );
     ```

- `guides.editor.canRunCommand(commandName, ...args)`：檢查命名的命令目前是否可以執行，而不實際執行。

  **簽章：**

  ```ts
  guides.editor.canRunCommand(commandName: string, ...args: any[]): boolean
  ```

  **範例：**

  ```js
  if (guides.editor.canRunCommand('surroundWithElement', 'sup')) {
    guides.editor.runCommand('surroundWithElement', 'sup');
  }
  ```

## 公用程式函式

- `guides.editor.runUtil(utilName, ...args)`：從新編輯器的公用程式登入叫用具名公用程式。 傳回公用程式的結果，或如果找不到公用程式，則傳回`undefined`。

  **簽章：**

  ```ts
  guides.editor.runUtil(utilName: string, ...args: any[]): any
  ```

  **可用的公用程式**

  >[!NOTE]
  >
  > 穩定性：下列公用程式是公用介面的一部分。 它們的名稱、簽章和可觀察的行為會視為穩定並保持相容性。 編輯器中可能會出現其他命令；但是，這些是內部命令，不適用於外部使用，可能會變更或移除，恕不另行通知。


  | 類別 | 公用程式 | 引數 | 傳回 | 說明 |
  |---|---|---|---|---|
  | 位置 | `getTextPos` | _（無）_ | `{ start: number, end: number }` | ProseMirror檔案中目前選取範圍的開始和結束位置 |
  | 位置 | `getNodePosition` | `position?: number` | `number` | 目前選取/焦點節點的檔案位置 |
  | 位置 | `mapToXpath` | `position: number` | `XPathPosition` | 將ProseMirror位置對應至XPath描述項 |
  | 位置 | `inverseMap` | `xpath: XPathPosition \| number` | `number` | 將XPath描述項（或數值位置）對應回ProseMirror位置 |
  | 文件 | `getNodeTree` | _（無）_ | `NodeTree \| null` | 檔案的樹狀表示，適用於輪廓演算 |
  | 文件 | `getAncestorsNames` | `position?: number` | `string[]` | 在`position`的上階節點的XML標籤名稱 |
  | 文件 | `getAncestorsDetails` | `position?: number` | `{ currNode: string, ancestors: Array<{tagName: string}>, previousSibling?: string, nextSibling?: string } \| undefined` | 目前節點、上階和位於`position`的直接同層級 |
  | 文件 | `getAncestorXpaths` | `includeId?: boolean` | `AncestorXpathItem[]` | 所有上階節點的XPath字串 |
  | 文件 | `getPreviousSibling` | `position?: number` | `string \| undefined` | 上一個同層級的標籤名稱（如果有的話） |
  | 文件 | `getNextSibling` | `position?: number` | `string \| undefined` | 下一個同層級的標籤名稱（如果有的話） |
  | 文件 | `getTagName` | `position?: number` | `string \| null` | 位於`position` （或游標）的元素標籤名稱 |
  | 元素搜尋 | `findPositionRange` | `tagName: string` | `{ from: number, to: number } \| undefined` | 具有指定標籤之第一個元素的範圍 |
  | 元素搜尋 | `findPositionRanges` | `tagName: string` | `Array<{ from: number, to: number }>` | 符合`tagName`之元素的所有範圍 |
  | 屬性 | `getAttributeAtPosition` | `position: number, attrName: string` | `unknown` | 從位於`position`的節點讀取XML屬性值 |
  | 屬性 | `getSerializableAttributes` | `xpath: string` | `Record<string, unknown>` | 位於`xpath`之節點的所有可序列化XML屬性 |
  | 序列化 | `serialize` | _（無）_ | `string` | 將整個檔案序列化為XML |
  | 序列化 | `serializeToText` | _（無）_ | `string` | 將整個檔案序列化為純文字 |
  | 序列化 | `getRangeXml` | `xpaths: AncestorXpathItem[]` | `string` | 傳回XPath定義範圍的XML |
  | 選擇 | `getSelectedXml` | _（無）_ | `string` | 目前選取的內容為XML字串 |
  | 選擇 | `getSelectedText` | _（無）_ | `string` | 選取的文字，不含任何標示 |
  | 選擇 | `hasSelection` | _（無）_ | `boolean` | 如果有使用中文字/節點選項，`true` |
  | 選擇 | `isSelectionEditable` | _（無）_ | `boolean` | 目前的選取範圍是否位於可編輯的內容內 |
  | 選擇 | `isPositionEditable` | `position: number` | `boolean` | `position`是否位於可編輯的內容內 |
  | 插入 | `canInsert` | `name: string, position?: number, insertMode?: 'after' \| 'before' \| 'rename'` | `boolean` | 是否可以在`position` （或游標）插入`name` |
  | 插入 | `getInsertPosition` | `name: string, position?: number, insertMode?: 'after' \| 'before' \| 'rename'` | `number \| null` | `name`的有效插入位置，若不可插入，則為`null` |
  | 插入 | `getNodeXml` | `nodeName: string, nodeContent?: string` | `string \| null` | 節點型別的XML範本 |
  | 換行/重新命名 | `getValidWrapNodeElementNames` | _（無）_ | `string[]` | 可包住目前選取範圍的元素名稱 |
  | 換行/重新命名 | `getValidRenameNodeElementNames` | _（無）_ | `string[]` | 可將目前節點的元素名稱重新命名為 |
  | 表格 | `getTableInfo` | `position?: number` | `{ rows: number, cols: number, header: number }` | 目前表格的尺寸 |
  | 標籤檢視 | `isTagViewActive` | _（無）_ | `boolean` | 標籤檢視呈現是否為使用中 |

  **範例：取得游標位置和上階名稱**

  ```js
  const textPos = guides.editor.runUtil("getTextPos");
  const ancestorNames = guides.editor.runUtil(
    "getAncestorsNames",
    typeof textPos === "number" ? textPos : undefined
  );
  ```

  **範例：尋找所有`<xref>`元素並讀取其屬性**

  ```js
  const xrefRanges = guides.editor.runUtil("findPositionRanges", "xref") || [];
  xrefRanges.forEach((range) => {
    const id = guides.editor.runUtil("getAttributeAtPosition", range.from, "id");
    const placeholderText = guides.editor.runUtil(
      "getAttributeAtPosition",
      range.from,
      "placeholdertext"
    );
  });
  ```

  **範例：尋找根元素範圍並讀取其屬性**

  ```js
  const rootRange = guides.editor.runUtil("findPositionRange", "concept"); // or "topic"
  if (rootRange) {
    const createdDate = guides.editor.runUtil(
      "getAttributeAtPosition",
      rootRange.from,
      "createdDate"
    );
    const author = guides.editor.runUtil(
      "getAttributeAtPosition",
      rootRange.from,
      "author"
    );
  }
  ```

  **範例：在作業之前檢查選取範圍並驗證上階內容**

  ```js
  const ancestorsDetails = guides.editor.runUtil('getAncestorsDetails');
  const selectedText = guides.editor.runUtil('getSelectedPlainText');
  const hasSelection = !!guides.editor.runUtil('hasSelection');
  
  const firstAncestor = ancestorsDetails?.currNode || ancestorsDetails?.ancestors?.[0]?.tagName;
  if (firstAncestor === 'ph') {
    tcx.util.showAlert("warning", "Operation is not allowed inside this element type.");
    return;
  }
  ```

  **範例：從上階XPath**&#x200B;取得專案ID

  ```js
  const ancestorItems = guides.editor.runUtil('getAncestorXpaths', true);
  for (const item of ancestorItems) {
    const attrs = guides.editor.runUtil('getSerializableAttributes', item.xpath);
    if (attrs?.id) { /* use element ID */ }
  }
  ```

## 裝飾API

裝飾API為編寫用於常見視覺自訂的完整ProseMirror外掛程式提供了更高級別的替代方案。 您不是手動管理`Plugin`、`PluginKey`和`DecorationSet`，而是描述&#x200B;*什麼*&#x200B;要裝飾和&#x200B;*如何*，編輯器的中央裝飾管理員會在內部處理ProseMirror狀態。

裝飾由字串`id`識別，因此可隨時獨立更新或移除。

>[!NOTE]
>
> **僅限新編輯器**&#x200B;這些API在舊版編輯器(`version === '1.0.0'`)上不具操作性。

- `guides.editor.addDecoration(id, selector, options)`：新增或取代裝飾規則。 所有符合目前檔案中`selector`的節點都將根據`options`進行裝飾。 每次檔案變更時，都會自動重新套用裝飾。

  **簽章：**

  ```ts
  guides.editor.addDecoration(
    id: string,
    selector: string,
    options: DecorationOptions
  ): boolean
  ```

  **`DecorationOptions`欄位：**

  | 欄位 | 類型 | 說明 |
  |---|---|---|
  | `class` | `string` | CSS類別名稱已新增至相符的節點 |
  | `computeAttributes` | `(node, context) => Record<string, string>` | 函式傳回每個節點的動態`data-*`或其他HTML屬性 |
  | `filter` | `(node) => boolean` | 選擇性述詞 — 只裝飾傳回`true`的節點 |

  傳遞至`computeAttributes`的`context`物件包括：
   - `index` — 在符合選取器的同層級中，以0為基礎的節點位置

  **範例：將CSS類別新增至所有`<section>`元素**

  ```js
  guides.editor.addDecoration('highlight-sections', 'section', {
    class: 'my-section-highlight'
  });
  ```

  **範例：新增計算的`data-number-label`屬性至每個區段**

  ```js
  guides.editor.addDecoration('section-numbers', 'section', {
    computeAttributes: (node, context) => ({
      'data-number-label': String(context.index + 1)
    })
  });
  ```

  **範例：只裝飾具有`importance="high"`屬性**&#x200B;的區段

  ```js
  guides.editor.addDecoration('important-sections', 'section', {
    class: 'section-important',
    filter: (node) => node.attrs?.xmlAttrs?.importance === 'high'
  });
  ```

  **範例：結合類別和計算屬性**

  ```js
  guides.editor.addDecoration('numbering-mode', 'conbody', {
    class: 'legacy-numbering'
  });
  
  guides.editor.addDecoration('section-numbers', 'section', {
    computeAttributes: (node, context) => ({
      'data-number-label': String(context.index + 1)
    })
  });
  ```

- `guides.editor.removeDecoration(id)`：移除先前依據其ID新增的裝飾。

  **簽章：**

  ```ts
  guides.editor.removeDecoration(id: string): boolean
  ```

  **範例：**

  ```js
  guides.editor.removeDecoration('section-numbers');
  ```

- `guides.editor.batchDecorations(changes)`：在單一ProseMirror傳送中套用多個新增/移除裝飾變更。 一次切換數個裝飾時請使用此選項，以避免重複轉譯。

  **簽章：**

  ```ts
  guides.editor.batchDecorations(changes: DecorationBatchChange[]): boolean
  
  type DecorationBatchChange =
    | { action: 'add', id: string, selector: string, options: DecorationOptions }
    | { action: 'remove', id: string }
  ```

  **範例：自動在兩個編號模式之間切換**

  ```js
  guides.editor.batchDecorations([
    { action: 'remove', id: 'legacy-numbering' },
    {
      action: 'add',
      id: 'division-numbering',
      selector: 'conbody',
      options: { class: 'division-numbering' }
    }
  ]);
  ```

  **範例：清除一個裝飾並新增兩個新裝飾**

  ```js
  guides.editor.batchDecorations([
    { action: 'remove', id: 'old-highlights' },
    {
      action: 'add',
      id: 'section-labels',
      selector: 'section',
      options: {
        computeAttributes: (node, ctx) => ({ 'data-section-index': String(ctx.index) })
      }
    },
    {
      action: 'add',
      id: 'note-style',
      selector: 'note',
      options: { class: 'styled-note' }
    }
  ]);
  ```

- `guides.editor.clearDecorations()`：移除裝飾管理員所管理的所有使用中裝飾。

  **簽章：**

  ```ts
  guides.editor.clearDecorations(): boolean
  ```

  **範例：**

  ```js
  guides.editor.clearDecorations();
  ```

- `guides.editor.getDecorations()`：傳回所有目前作用中裝飾的ID。

  **簽章：**

  ```ts
  guides.editor.getDecorations(): string[]
  ```

  **範例：**

  ```js
  const active = guides.editor.getDecorations();
  console.log('Active decorations:', active);
  // e.g. ['section-numbers', 'numbering-mode', 'note-style']
  ```


### 裝飾API與`registerPlugin`

| 情境 | 使用 |
|---|---|
| 將CSS類別或`data-*`屬性套用至相符的元素 | `addDecoration` |
| 根據執行階段狀態（中繼資料、使用者動作）切換或更新樣式 | `addDecoration` / `removeDecoration` / `batchDecorations` |
| 複雜的外掛程式邏輯：自訂狀態、索引鍵繫結、Widget裝飾、事件處理常式 | `registerPlugin` |
| 將CSS插入影子DOM | `registerPlugin`與`css`欄位 |


## ProseMirror外掛程式註冊

- `guides.editor.registerPlugin(factory)`：註冊要包含在每個New Editor執行個體中的ProseMirror外掛程式工廠。 只接受原廠功能，拒絕直接外掛程式執行個體。 每個編輯器執行個體會呼叫一次Factory，以確保隔離的外掛程式狀態。

  **簽章：**

  ```ts
  guides.editor.registerPlugin(factory: () => PluginConfig): void
  
  interface PluginConfig {
    plugin: ProseMirrorPlugin | ProseMirrorPlugin[]
    css?: string  // Injected into editor's shadow DOM
  }
  ```

  **範例：在編輯器準備就緒後註冊外掛程式**

  ```js
  guides.ready(() => {
    guides.editor.registerPlugin(createNumberingPlugin);
    guides.editor.registerPlugin(createXrefPlugin);
  });
  ```

  **範例：使用CSS的內嵌工廠**

  ```js
  guides.editor.registerPlugin(() => ({
    plugin: new guides.editor.prosemirror.state.Plugin({
      key: new guides.editor.prosemirror.state.PluginKey("myPlugin"),
      props: {
        decorations(state) {
          // return DecorationSet...
        }
      }
    }),
    css: `.my-decoration { background: yellow; }`
  }));
  ```

  >[!NOTE]
  >
  > 透過`css`傳遞的CSS會插入編輯器的影子DOM。 一般頁面層級樣式表不會套用至編輯器內。

## ProseMirror程式庫

- `guides.editor.prosemirror`：直接公開ProseMirror套件以用於外掛程式開發。 這可避免在擴充功能程式碼中單獨捆綁ProseMirror。

  | 屬性 | 封裝 |
  |---|---|
  | `state` | `prosemirror-state` |
  | `model` | `prosemirror-model` |
  | `view` | `prosemirror-view` |
  | `transform` | `prosemirror-transform` |
  | `commands` | `prosemirror-commands` |
  | `keymap` | `prosemirror-keymap` |
  | `history` | `prosemirror-history` |
  | `tables` | `prosemirror-tables` |
  | `dropcursor` | `prosemirror-dropcursor` |
  | `markdown` | `prosemirror-markdown` |

  **範例：建立節點裝飾外掛程式**

  ```js
  const myPluginKey = new guides.editor.prosemirror.state.PluginKey("myPlugin");
  
  const createMyPlugin = () => {
    const { Plugin } = guides.editor.prosemirror.state;
    const { Decoration, DecorationSet } = guides.editor.prosemirror.view;
  
    return {
      plugin: new Plugin({
        key: myPluginKey,
        state: {
          init() { return { enabled: true }; },
          apply(tr, value) {
            const meta = tr.getMeta(myPluginKey);
            return meta ? { ...value, ...meta } : value;
          }
        },
        props: {
          decorations(state) {
            const decorations = [];
            state.doc.descendants((node, pos) => {
              if (node.type.name === "section") {
                decorations.push(
                  Decoration.node(pos, pos + node.nodeSize, { class: "my-section" })
                );
              }
            });
            return DecorationSet.create(state.doc, decorations);
          }
        }
      }),
      css: `.my-section { border-left: 3px solid #ccc; padding-left: 8px; }`
    };
  };
  ```

  **範例：建立Widget裝飾外掛程式（內嵌顯示文字）**

  ```js
  const xrefPluginKey = new guides.editor.prosemirror.state.PluginKey("xrefDisplay");
  
  const createXrefPlugin = () => {
    const { Plugin } = guides.editor.prosemirror.state;
    const { Decoration, DecorationSet } = guides.editor.prosemirror.view;
  
    return {
      plugin: new Plugin({
        key: xrefPluginKey,
        props: {
          decorations(state) {
            const decorations = [];
            state.doc.descendants((node, pos) => {
              if (node.type.name.includes("xref")) {
                const display = node.attrs?.xmlAttrs?.placeholdertext;
                if (display) {
                  decorations.push(
                    Decoration.widget(pos + 1, () => {
                      const el = document.createElement("span");
                      el.textContent = `[${display}]`;
                      el.setAttribute("contenteditable", "false");
                      return el;
                    }, { key: `xref-${pos}` })
                  );
                }
              }
            });
            return DecorationSet.create(state.doc, decorations);
          }
        }
      }),
      css: `.xref-display-text { color: #0074d9; pointer-events: none; }`
    };
  };
  ```

## 將CSS插入編輯器中

參考線DITA編輯器會從類別為`apps.guides.dita_editor.content`的clientlib載入其作者模式內容樣式。 該clientlib有一個`embed`宣告，可自動提取類別下註冊的任何clientlib：

```
apps.guides.xml_editor.dita_content_overrides
```

若要將自訂CSS插入編輯器的內容區域，請建立具有此類別的AEM clientlib節點。 不需要額外佈線，當編輯器頁面載入時，「參考線」會自動選取它。

**AEM clientlib節點結構(`/apps/my-extension/clientlibs/editor-content-overrides/.content.xml`)**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
    jcr:primaryType="cq:ClientLibraryFolder"
    categories="[apps.guides.xml_editor.dita_content_overrides]"/>
```

將您的CSS檔案（`css.txt` +您的`.css`檔案）放在此資料夾中。 它會自動內嵌在編輯器的內容樣式表中。

**範例：在作者模式中覆寫章節標題樣式**

```css
/* /apps/my-extension/clientlibs/editor-content-overrides/css/content.css */

/* Increase section title font size in author mode */
.section > title {
  font-size: 1.4em;
  font-weight: bold;
  color: #333;
}

/* Highlight note blocks */
.note {
  border-left: 4px solid #0074d9;
  padding-left: 12px;
  background: #f0f7ff;
}
```

>[!NOTE]
>
>此CSS僅將目標定位為舊版以CKEditor為基礎的作者表面。 它在使用影子DOM的新編輯器(ProseMirror)內沒有作用。


### 新編輯器： `registerPlugin`中的`css`

新編輯器會在&#x200B;**陰影DOM**&#x200B;內轉譯，這會將其與所有頁面層級樣式（包括AEM `clientlibs`）隔離。 若要將CSS插入NEW Editor的作者介面，請傳遞`css`字串作為外掛程式工廠傳回的`PluginConfig`的一部分。

每次建立編輯器執行個體時，CSS都會直接插入編輯器的陰影根目錄中作為`<style>`標籤。

**範例：將樣式與裝飾外掛程式一起插入**

```js
guides.ready(() => {
  guides.editor.registerPlugin(() => ({
    plugin: createMyPlugin(), // your ProseMirror plugin
    css: `
      /* Styles scoped to the New Editor shadow DOM */
      .section > .title-node {
        font-size: 1.4em;
        font-weight: bold;
        color: #333;
      }

      .note-node {
        border-left: 4px solid #0074d9;
        padding-left: 12px;
        background: #f0f7ff;
      }
    `
  }));
});
```

**範例：僅限CSS的外掛程式（無裝飾邏輯）**

```js
guides.ready(() => {
  guides.editor.registerPlugin(() => ({
    plugin: new guides.editor.prosemirror.state.Plugin({}), // no-op plugin
    css: `
      /* Custom author-mode typography */
      [data-xml-element="codeblock"] {
        font-family: monospace;
        background: #f5f5f5;
        padding: 8px;
        border-radius: 4px;
      }
    `
  }));
});
```

>[!NOTE]
>
> 此CSS只適用於新編輯器陰影DOM。 它不會影響頁面的其餘部分或舊版編輯器。


## 內容功能表副檔名(`contextMenuWidget`)

擴充功能可在其擴充功能設定中宣告`contextMenuWidget`欄位，以將專案新增至編輯器的滑鼠右鍵/階層連結內容功能表。 這會告訴框架要鎖定哪個編輯器的功能表。

### Widget ID

| Widget ID | 編輯器 |
|---|---|
| `dita_editor_menu` | 舊版CKEditor作者表面（階層連結+元素內容功能表） |
| `markup_editor_menu` | 新增編輯器(ProseMirror)階層連結和元素快顯功能表 |

兩個Widget會同時掛接在頁面上。 根據此欄位，框架會將每個擴充功能配對至正確的功能表。

> 擴充功能也可以透過傳遞陣列來鎖定兩個編輯器： `contextMenuWidget: ["dita_editor_menu", "markup_editor_menu"]`

### 舊版編輯器： `dita_editor_menu`

請將此用於應該出現在舊版CKEditor內容功能表中的擴充功能。

```js
const myContextMenuExtension = {
  id: "dita_author_view_menu",
  contextMenuWidget: "dita_editor_menu",
  view: {
    items: [
      {
        displayName: "My Custom Action",
        data: { eventid: "myCustomAction" },
        icon: "textSpaceAfter",
        target: {
          key: "displayName",
          value: "Wrap Element",   // insert after this existing menu item
          viewState: "append",
        },
      },
    ],
  },
  controller: {
    myCustomAction() {
      console.log("Custom action triggered");
    },
  },
};
```

### 新編輯器： `markup_editor_menu`

將此用於應出現在新編輯器快顯功能表（階層連結和按一下右鍵元素）中的擴充功能。 控制器透過`handleExtensionEvent`接收事件，這會將本機處理常式路由到`markup_editor_menu`控制器，並透過應用程式事件處理常式分派全域事件。

```js
const myMarkupContextMenu = {
  id: "dita_author_view_menu",
  contextMenuWidget: "markup_editor_menu",
  view: {
    items: [
      {
        displayName: "Edit Cross Reference",
        data: { eventid: "editCrossReference" },
        icon: "link",
        target: {
          key: "displayName",
          value: "Cut",
          viewState: "prepend",
        },
      },
      {
        displayName: "Remove Cross Reference",
        data: { eventid: "removeCrossReference" },
        icon: "deleteOutline",
        target: {
          key: "displayName",
          value: "Edit Cross Reference",
          viewState: "append",
        },
      },
    ],
  },
  controller: {
    editCrossReference() {
      // Use guides.editor APIs to read context
      const ancestorXpaths = guides.editor.runUtil("getAncestorXpaths", true);
      // open dialog or take action...
    },
    removeCrossReference() {
      guides.editor.runCommand("unwrapNode");
    },
  },
};
```

## 公用程式庫

- `guides.util.lodash`:The lodash公用程式程式庫，編輯器隨附相同的執行個體。

  ```js
  const uniqueIds = guides.util.lodash.uniq(ids);
  ```

- `guides.util.async`：用於擴充功能的非同步公用程式庫。

  ```js
  guides.util.async.parallel([task1, task2], callback);
  ```

## 完整API參考

| API | 說明 |
|---|---|
| `filePath` | 取得使用中檔案的檔案路徑 |
| `version` | 取得載入的編輯器版本字串 |
| `appState(key)` | 從應用程式模型讀取值 |
| `focus()` | 聚焦作用中編輯器 |
| `canInsertXmlElement(tag, insertAfter?)` | 檢查是否可在游標處插入元素 |
| `selectCurrentBlockElement()` | 選取目前的區塊元素 |
| `getValidElementNamesForInsertion(args)` | 列出要插入的有效元素名稱 |
| `updateAttributeByXpath(args)` | 依XPath更新屬性 |
| `runCommand(name, ...args)` | 執行具名編輯器命令 |
| `canRunCommand(name, ...args)` | 檢查命令是否可以執行 |
| `runUtil(name, ...args)` | 叫用具名編輯器公用程式 |
| `addDecoration(id, selector, options)` | 在相符的元素上新增或取代已命名的裝飾規則 |
| `removeDecoration(id)` | 依ID移除裝飾規則 |
| `batchDecorations(changes)` | 在一個分派中套用多個新增/移除裝飾變更 |
| `clearDecorations()` | 移除所有作用中的裝飾規則 |
| `getDecorations()` | 取得所有目前作用中裝飾的ID |
| `registerPlugin(factory)` | 註冊ProseMirror外掛程式工廠（也是陰影DOM CSS插入的機制） |
| `prosemirror.state` | `prosemirror-state`封裝 |
| `prosemirror.model` | `prosemirror-model`封裝 |
| `prosemirror.view` | `prosemirror-view`封裝 |
| `prosemirror.transform` | `prosemirror-transform`封裝 |
| `prosemirror.commands` | `prosemirror-commands`封裝 |
| `prosemirror.keymap` | `prosemirror-keymap`封裝 |
| `prosemirror.history` | `prosemirror-history`封裝 |
| `prosemirror.tables` | `prosemirror-tables`封裝 |
| `prosemirror.dropcursor` | `prosemirror-dropcursor`封裝 |
| `prosemirror.collab` | `prosemirror-collab`封裝 |
| `prosemirror.markdown` | `prosemirror-markdown`封裝 |
