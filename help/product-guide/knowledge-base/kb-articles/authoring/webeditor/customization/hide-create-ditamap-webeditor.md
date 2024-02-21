---
title: 針對特定使用者或群組，在資料夾快顯功能表選項中隱藏建立DitaMap選項。
description: 瞭解如何透過隱藏特定使用者/群組的資料夾快顯選單中的「DitaMap」選項來自訂編輯器
source-git-commit: ea8fb646287f68676b6530b4cc5f56e7ba2d9b0c
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# 在編輯器中從資料夾內容選單顯示/隱藏「建立DitaMAP」

在本文中，我們將瞭解如何根據使用者/群組許可權，自訂Guides網頁編輯器，以隱藏或顯示檔案夾快顯選單中的「建立DitaMap」選項。
在此使用案例中，我們將為所有非作者使用者隱藏此選項。

## 先決條件

我們將運用AEM Guides擴充功能套件，該套件可讓您根據自己的需求自訂應用程式的UI。
請詳閱以下內容 [檔案](https://github.com/adobe/guides-extension/tree/main) 以深入瞭解Guides擴充功能框架的運作方式。

現在開始瞭解如何自訂資料夾快顯功能表，以針對所有非作者使用者隱藏此選項。

您可從下方的程式碼片段中看到，作者使用者可看到「建立DitaMap」選項。

![顯示建立DitaMap選項](../../../assets/authoring/ditamap-show-author.png)

現在來看看如何使用Guides擴充功能框架隱藏此選項。

## 實作步驟

實作分為下列部分：

- **Folder_options控制器中的變更**

  每個內容功能表都有一個關聯的控制器ID。 此控制器會處理各種內容功能表選項的事件上功能。

  在此範例中，我們將自訂資料夾快顯選單以隱藏非作者的「建立DitaMap」選項。 為此，我們將變更guides擴充功能框架存放庫中/src底下的folder_options.ts檔案。

  我們使用「viewState」作為「REPLACE」來隱藏內容選單中的此選項。
我們正在透過索引鍵「id」呼叫此folder_options中的新Widget。

```typescript
const folderOptions = {
  id: "folder_options",
  contextMenuWidget: "repository_panel",
  view: {
    items: [
      {
        component: "widget",
        id: "customditamap",
        target: {
          key: "displayName",
          value: "DITA Map",
          viewState: VIEW_STATE.REPLACE,
        },
      },
    ],
  },
};
```

- **建立新Widget以處理邏輯**

  需要建立新的Widget (customoptions.ts)來寫入邏輯，以僅針對非編寫使用者隱藏此選項。 為此，我們使用了「show」鍵，作為JSON結構中的切換。

  您可以編寫自己的外部servlet來檢查群組詳細資訊。 如此一來，您也可以自訂自訂群組的資料夾功能表選項。
在此範例中，我們已運用OOTB AEM &#39;rolesapi&#39;呼叫來擷取使用者詳細資訊，並在&#39;isAuthor&#39;中設定回應，如上述程式碼片段所示。

```typescript
const folderOptions = {
  id: "customditamap",
  view: {
    component: "button",
    quiet: true,
    icon: "breakdownAdd",
    label: "DITA Map",
    "on-click": "createNewDitaMap",
    show: "@extraProps.isAuthor",
  },
};
```

透過，我們能夠根據「show」的值隱藏標籤為「Dita Map」的按鈕。

我們已新增控制器，以便在模型中設定「isAuthor」屬性，這可以在控制器中使用下列語法完成。

```typescript
this.model.extraProps.set("key", value);
```

鍵值為「isAuthor」，值為來自rolesapi呼叫的回應。
我們也定義了「createNewDitaMap」事件以啟用「建立DitaMap」選項（適用於作者使用者）。

```typescript
controller: {
    init: function () {
      this.model.extraProps.set("isAuthor", false);

      rolesApiResponse.then((result) => {
        console.log(result);
        this.model.extraProps.set(
          "isAuthor",
          result["/content/dam"].roles.authors
        );

        console.log("testresult" + result["/content/dam"].roles.authors);
      });
    },
    createNewDitaMap() {
      repositoryController && repositoryController.next("create_new.map");
    },
  },
```

- **新增自訂程式碼**

  將folder_options.ts和customoptions.ts匯入/src下的index.ts檔案中。

## 測試

- 以不屬於作者群組的使用者登入AEM。 建立DitaMap選項會隱藏在任何資料夾的內容功能表中，如下所示。
此使用案例已新增至GIT，請尋找以下相關資源。

![隱藏建立DitaMap選項](../../../assets/authoring/ditamap-hide-non-author.png)

### 相關資源

- **Extension Framework基本存放庫** - [GIT](https://github.com/adobe/guides-extension/tree/main)

- **檔案** - [在Experience League上](../../../../../guides-ui-extensions/aem_guides_framework/basic-customisation.md)

- **記錄常見的使用案例** - [在Experience League上](../../../../../guides-ui-extensions/aem_guides_framework/jui-framework.md)

- **有範例的公共存放庫** - [在GIT上](https://github.com/adobe/guides-extension/tree/sc-expert-session). 請參閱分支sc-expert-session

```

```
