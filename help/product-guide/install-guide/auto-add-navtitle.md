---
title: 預設包含@navtitle屬性
description: 瞭解如何依預設包含@navtitle屬性
exl-id: 3def20dc-dd24-4526-ae36-45708249d34a
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 1%

---

# 預設包含@navtitle屬性 {#id2115BC0J0XA}

您可以在地圖中新增不同型別的參考檔案，例如主題、參考、任務、\(sub\)地圖等等。 這些檔案大多支援`@navtitle`屬性。 不過，一致使用它的作者並不多。 如果您要在地圖中所有參照的檔案中強制使用`@navtitle`屬性，則可以使用簡單的設定來執行。

啟用後，您在對應中新增的每個參考檔案都會自動將`@navtitle`屬性新增至其屬性。 `@navtitle`也會取得參考內容的`title`專案值。

若要在參考檔案的屬性中預設包含`@navtitle`屬性，請執行下列步驟：

1. 下載ui\_config.json檔案。

   您可以在全域層級或檔案夾層級設定檔中進行此變更。 視您想要進行此變更的位置而定，您需要下載個別的ui\_config.json檔案。 如需有關下載ui\_config.json檔案的詳細資訊，請參閱[設定和自訂XML Web編輯器](conf-folder-level.md#id2065G300O5Z)。

1. 搜尋`ditaAttributes`定義。

   `ditaAttributes`的預設定義為：

   ```json
   "ditaAttributes": {
   "attributes": [],
   "constraint": false,
   "required": {}
   },
   ```

1. 將`required`引數變更為：

   ```json
   "required": {"navtitle": true}
   ```

1. 儲存檔案。

1. 將檔案上傳至對應的設定檔\（全域或資料夾\）。


透過此設定，您新增至對應的每個參考檔案依預設將包含`@navtitle`屬性。
