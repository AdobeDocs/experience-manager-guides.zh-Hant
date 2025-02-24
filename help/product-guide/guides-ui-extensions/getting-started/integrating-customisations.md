---
title: 安裝及設定
description: 安裝和使用AEM Guides擴充功能套件
role: User, Admin
exl-id: 0304c8d0-35a8-4712-a9af-36557e3b247f
source-git-commit: b4d6c1c8c2d413bb4137e58391554abf2fb68b8c
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# 安裝和使用AEM Guides擴充功能套件

擴充功能可讓您自訂AEM Guides應用程式，以更符合您的需求。 AEM Guides v4.3以上（內部部署）和2310 （雲端）支援此擴充功能框架。

## 要求

此封裝需要[Git Bash](https://github.com/git-guides/install-git)和npm

## 安裝

啟動AEM Guides框架安裝的最簡單方法就是透過cli

```bash
npx @adobe/create-guides-extension
```

## 新增自訂程式碼

1. 在`src/`目錄中為您要擴充的每個元件新增程式碼檔案。 已經為您新增了一些範例檔案。
2. 現在在位於`src/`目錄中的`index.ts`檔案中：
   - 匯入`.ts`檔案，其中包含您要在組建中新增的自訂。
   - 新增匯入至`window.extension`
   - 註冊自訂元件的`id`並對應的`tcx extensions`匯入
   - 請參閱範例`/src/index.ts`

## 建立自訂程式碼

- 在根目錄中執行`npm run build`。 您將在目錄`dist/`中取得3個檔案：
   - `build.css`
   - `guides-extension.js`
   - `guides-extension.umd.cjs`

![建置輸出](./../imgs/build_output.png)

## 新增自訂至AEM

- 移至`CRXDE` `crx/de/index.jsp#/`
- 在`apps`資料夾下，建立型別`cq:ClientLibraryFolder`的新節點

![資料夾結構](./../imgs/crxde_folder_structure.png)

- 在節點的`properties`中，選取`Multi`新增下列屬性
名稱： `categories`
型別： `String []`
值： `apps.fmdita.review_overrides`， `apps.fmdita.xml_editor.page_overrides`

>[!NOTE]
>
> 對於倒數第二個UI，值為： `apps.fmdita.penultimate.xml_editor.page_overrides`和`apps.fmdita.review_overrides`


![資料夾屬性](./../imgs/crxde_folder_properties.png)

- 若要新增內建js，請建立新檔案，例如，在上述建立的節點中`tcx1.js`。 在這裡，新增來自`dist/guides-extension.umd.cjs`或`dist/guides-extension.js`的程式碼。 現在建立新檔案`js.txt`，我們在這裡新增js檔案的名稱，在此案例中會是：

```t
#base=.
tcx1.js
```

- 若要新增內建的css，請建立新檔案，例如`tcx1.css`在上述建立的節點中。 在這裡，新增來自`dist/build.css`的程式碼。 現在建立新檔案`css.txt`，在此加入我們的css檔案名稱，在此案例中會是：

```t
#base=.
tcx1.css
```

- 執行`shift + refresh`以載入包含自訂內容的應用程式！

## 疑難排解

檢查上述所有步驟是否正確執行。
將程式碼新增至tcx.js後，請務必執行強制重新整理(shift+refresh)。
現在開啟AEM，按一下滑鼠右鍵並按一下`Inspect`
移至[來源]並搜尋您的`[node_name].js` （例如： extensions.js）檔案。 執行Control / Cmd + D以搜尋您的檔案。 如果存在包含您從`dist/guides-extension.umd.cjs`或`dist/guides-extension.js`貼上之JS程式碼的`.js`檔案，表示您的設定已完成
