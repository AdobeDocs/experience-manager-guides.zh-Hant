---
title: 預設包含@navtitle屬性
description: 瞭解如何依預設包含@navtitle屬性
exl-id: 38711c0c-efa8-461a-92e1-ecfcdcdd36d3
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: a3c7973868549c72e868c05a3fc6ca8bdce9bce3
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 預設包含@navtitle屬性 {#id2115BC0J0XA}

您可以在地圖中新增不同型別的參考檔案，例如主題、參考、任務、\(sub\)地圖等等。 這些檔案大多支援`@navtitle`屬性。 不過，一致使用它的作者並不多。 如果您要在地圖中所有參照的檔案中強制使用`@navtitle`屬性，則可以使用簡單的設定來執行。

啟用後，您在對應中新增的每個參考檔案都會自動將`@navtitle`屬性新增至其屬性。 `@navtitle`也會取得參考內容的`title`專案值。

若要在參考檔案的屬性中預設包含`@navtitle`屬性，請執行下列步驟：

1. 若要下載UI設定檔，請以管理員身分登入Adobe Experience Manager。

1. 按一下頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取&#x200B;**指南**，然後按一下&#x200B;**資料夾設定檔**。
1. 按一下&#x200B;**全域設定檔**&#x200B;圖磚。
1. 選取&#x200B;**XML編輯器設定**&#x200B;索引標籤，然後按一下頂端的&#x200B;**編輯**&#x200B;圖示
1. 按一下「**下載**」圖示，在本機系統上下載ui\_config.json檔案。
1. 您可以在全域層級或檔案夾層級設定檔中進行此變更。 視您想要進行此變更的位置而定，您需要下載個別的ui\_config.json檔案。 如需有關下載ui\_config.json檔案的詳細資訊，請參閱[設定和自訂XML Web編輯器](conf-folder-level.md#id2065G300O5Z)。

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



**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](conf-web-editor.md)
