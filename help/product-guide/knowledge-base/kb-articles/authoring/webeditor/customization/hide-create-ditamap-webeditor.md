---
title: 針對特定使用者或群組，在資料夾快顯功能表選項中隱藏建立DitaMap選項。
description: 瞭解如何透過隱藏特定使用者/群組的資料夾快顯選單中的「DitaMap」選項來自訂編輯器
exl-id: 796bfe3a-3950-4ade-9215-c33534791055
TQID: https://experienceleague.adobe.com/fAMBEOKlPA4KHsE81zfI-6EJ6zwaQOgRfx0w-cx-mmw
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: 444
ht-degree: 1%

---

# 在編輯器中從資料夾內容選單顯示/隱藏「建立DitaMAP」

在本文中，我們將瞭解如何根據使用者/群組許可權，自訂「參考線編輯器」以在資料夾快顯選單中隱藏或顯示「建立DitaMap」選項。
在此使用案例中，我們將為所有非作者使用者隱藏此選項。

## 必要條件

我們將運用AEM Guides擴充功能套件，該套件可讓您根據自己的需求自訂應用程式的UI。
請參閱此[檔案](https://github.com/adobe/guides-extension/tree/main)，深入瞭解Guides擴充功能架構的運作方式。

現在開始瞭解如何自訂資料夾快顯功能表，以針對所有非作者使用者隱藏此選項。

您可從下方的程式碼片段中看到，作者使用者可看到「建立DitaMap」選項。

![顯示建立DitaMap選項](../../../assets/authoring/ditamap-show-author.png)

現在來看看如何使用Guides擴充功能框架隱藏此選項。

## 實施步驟

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

- **建立新的Widget以處理邏輯**

  需要建立新的Widget (customoptions.ts)來寫入邏輯，以僅針對非編寫使用者隱藏此選項。 為此，我們使用了「show」鍵，作為JSON結構中的切換。

  您可以編寫自己的外部servlet來檢查群組詳細資訊。如此一來，您也可以自訂自訂群組的資料夾功能表選項。
在此範例中，我們已運用OOTB AEM「rolesapi」呼叫來擷取使用者詳細資訊，並在「isAuthor」中設定回應，如上述程式碼片段所示。

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

- **正在新增自訂程式碼**

  將folder_options.ts和customoptions.ts匯入/src下的index.ts檔案中。

## 測試

- 以不屬於作者群組的使用者登入AEM。建立DitaMap選項會隱藏在任何資料夾的內容功能表中，如下所示。
此使用案例已新增至GIT，請尋找以下相關資源。

![隱藏建立DitaMap選項](../../../assets/authoring/ditamap-hide-non-author.png)

### 相關資源

- **擴充框架基本存放庫** - [GIT](https://github.com/adobe/guides-extension/tree/main)

- 在Experience League[&#128279;](../../../../../guides-ui-extensions/aem_guides_framework/basic-customisation.md)上&#x200B;**檔案** - 

- **在Experience League[&#128279;](../../../../../guides-ui-extensions/aem_guides_framework/jui-framework.md)上記錄常見使用案例** - 

- 在GIT[&#128279;](https://github.com/adobe/guides-extension/tree/sc-expert-session)上有&#x200B;**公開存放庫（含樣本）** - 。 請參閱分支sc-expert-session

```

```
