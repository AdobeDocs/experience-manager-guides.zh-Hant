---
title: 預設包含@navtitle屬性
description: 瞭解如何依預設包含@navtitle屬性
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 1%

---

# 預設包含@navtitle屬性 {#id2115BC0J0XA}

您可以在地圖中新增不同型別的參考檔案，例如主題、參考、任務、\(sub\)地圖等等。 這些檔案大多支援`@navtitle`屬性。 不過，一致使用它的作者並不多。 如果您要在地圖中所有參照的檔案中強制使用`@navtitle`屬性，則可以使用簡單的設定來執行。

啟用後，您在對應中新增的每個參考檔案都會自動將`@navtitle`屬性新增至其屬性。 `@navtitle`也會取得參考內容的`title`專案值。

下列標籤會提供根據您的Experience Manager Guides設定，在參考檔案的屬性中預設包含`@navtitle`屬性的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 若要下載UI設定檔，請以管理員身分登入Adobe Experience Manager。
1. 按一下頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取&#x200B;**指南**，然後按一下&#x200B;**資料夾設定檔**。
1. 按一下&#x200B;**全域設定檔**&#x200B;圖磚。
1. 選取&#x200B;**XML編輯器設定**&#x200B;索引標籤，然後按一下頂端的&#x200B;**編輯**&#x200B;圖示
1. 按一下「**下載**」圖示，在本機系統上下載ui\_config.json檔案。
1. 您可以在全域層級或檔案夾層級設定檔中進行此變更。 視您想要進行此變更的位置而定，您需要下載個別的ui\_config.json檔案。 如需有關下載ui\_config.json檔案的詳細資訊，請參閱[設定和自訂XML Web編輯器](conf-profiles.md#id2065G300O5Z)。

1. 搜尋`ditaAttributes`定義。

   `ditaAttributes`的預設定義為：

   ```
   "ditaAttributes": {
                           "attributes": [],
                           "constraint": false,
                           "required": {}
                           },
   ```

1. 變更`required`引數，如下所示：

   ```
   "required": {"navtitle": true}
   ```

   設定為`true`時，會啟用&#x200B;**重新整理導覽標題屬性**&#x200B;按鈕，使其顯示在編輯器工具列中。 當設定為`false`或保持空白時，按鈕在編輯器中保持隱藏。
1. 儲存檔案。

1. 將檔案上傳至對應的設定檔\（全域或資料夾\）。


透過此設定，您新增至對應的每個參考檔案依預設將包含`@navtitle`屬性。

>[!TAB 內部部署]

1. 下載ui\_config.json檔案。

   您可以在全域層級或檔案夾層級設定檔中進行此變更。 視您想要進行此變更的位置而定，您需要下載個別的ui\_config.json檔案。 如需有關下載ui\_config.json檔案的詳細資訊，請參閱[設定和自訂XML Web編輯器](conf-profiles.md#id2065G300O5Z)。

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

>[!ENDTABS]

**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](customize-overview.md)
