---
title: 自訂工具列
description: 瞭解如何自訂工具列
exl-id: ba82af48-9357-4f29-90ce-6793366ab432
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 0%

---

# 自訂工具列 {#id172FB00L0V6}

依預設，Web編輯器會隨附任何DITA編輯器所需的最常見編輯功能。 編輯器中有插入型別清單\（編號或專案符號\）、互動參照、內容參照、表格、段落和字元格式等元素的功能。 除了這些基本元素之外，您還可以自訂Web編輯器來插入在編寫環境中使用的元素。

自訂網頁編輯器的工具列有兩種方式：

- 將新功能新增至工具列

- 從工具列移除任何現有功能


## 在工具列中新增功能

將功能新增至網頁編輯器涉及兩個主要工作 — 在&#x200B;*ui\_config.json*&#x200B;檔案中新增該功能的圖示，以及在JavaScript中新增背景功能。

執行以下步驟，將功能新增至網頁編輯器的工具列：

1. 若要下載UI設定檔，請以管理員身分登入Adobe Experience Manager。

1. 按一下頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取&#x200B;**參考線**，然後按一下&#x200B;**資料夾設定檔**。
1. 按一下&#x200B;**全域設定檔**&#x200B;圖磚。
1. 選取&#x200B;**XML編輯器設定**&#x200B;索引標籤，然後按一下頂端的&#x200B;**編輯**&#x200B;圖示
1. 按一下「**下載**」圖示，在本機系統上下載ui\_config.json檔案。 您可以接著對檔案進行變更，然後上傳相同的檔案。
1. 在`ui_config.json`檔案中，在工具列區段中新增新功能的定義。 儲存檔案並上傳。

   通常，您可以建立新的工具列按鈕群組，並在其中新增一或多個工具列按鈕。 或者，您可以在現有的工具列群組中新增工具列按鈕。 建立新的工具列群組需要下列詳細資料：

   **型別**：   指定`blockGroup`為`type`值。 此值表示您正在建立包含一或多個工具列群組的區塊群組。

   **extraclass**：   以空格分隔的一或多個類別的名稱。

   **個專案**：   在工具列中指定所有群組的定義。 每個群組可以包含一或多個工具列圖示。 若要定義工具列群組中的圖示，您必須在`items`中重新定義`type`屬性，並將其值設為`buttonGroup`。 在`extraclass`屬性中指定一或多個類別名稱。 在`label`屬性中指定功能名稱。 `ui_config.json`檔案中的下列程式碼片段顯示主要工具列區塊的定義，後面接著`buttonGroup`定義：

       「
」       「工具列」： {
       &quot;type&quot;： &quot;blockGroup&quot;，
       「extraclass」：
       「工具列作業」，
       「專案」： [
       {
       &quot;type&quot;： &quot;buttonGroup&quot;，
       &quot;extraclass&quot;： &quot;left-controls&quot;，
       &quot;label&quot;： &quot;Left Controls&quot;，
       「專案」： [
       「
」   
   在`items`集合中，您必須指定一或多個工具列圖示的定義。

   您需要定義以下屬性以新增工具列圖示：

   **型別**：   指定`button`為`type`值。 此值表示您正在新增工具列按鈕。

   **圖示**：   指定您要在工具列中使用的Coral圖示名稱。

   **變體**：   指定`quiet`為`variant`值。

   **標題**：   指定圖示的工具提示。

   **點按**：   在JavaScript檔案中指定為特徵定義的指令名稱。 如果您的命令需要輸入引數，則指定命令名稱為：

       ``Javascript
       &quot;on-click&quot;： {&quot;name&quot;： &quot;AUTHOR_INSERT_ELEMENT&quot;， &quot;args&quot;： &quot;simpletable&quot;}
       「
」   
   **顯示或隱藏**：   如果您正在定義`show`屬性，請指定圖示的顯示模式。 可能的值為 — `@isAuthorMode`、`@isSourceMode`、`@isPreviewMode`、`true` \（在所有模式中顯示\）或`false` \（在所有模式中隱藏\）。

   您也可以定義`hide`屬性，以取代`show`。 可能的值與`show`屬性中的值相同，唯一差異在於指定的模式不會顯示圖示。

   以下範例顯示使用者按一下工具列中的「顯示版本」圖示時的AEM Guides版本號碼。

   將下列程式碼新增至JavaScript檔案：

   ```Javascript
   $(document).ready(setTimeout(function() {
                           fmxml.commandHandler.subscribe({
                           key: 'user.alert',
                           next: function() {
                           alert("AEM Guides version x.x")
                           }
                           })
                           }, 1000))
   ```

   在&#x200B;*ui\_config.json*&#x200B;檔案中新增功能，如下所示：

   ```Javascript
   "type": "button",
   "icon": "alert","variant": "quiet","title": "About AEM Guides","show": "true","on-click": "user.alert"
   ```

1. 建立&#x200B;*clientlib*&#x200B;資料夾，並將您的JavaScript新增至此資料夾。

1. 透過將&#x200B;*apps.fmdita.xml\_editor.page\_overrides*&#x200B;的值指派給&#x200B;*clientlib*&#x200B;資料夾來更新categories屬性。

1. 儲存&#x200B;*ui\_config.json*&#x200B;檔案並重新載入網頁編輯器。


## 從工具列移除功能

有時您可能不想提供網頁編輯器中目前可用的所有功能，在這種情況下，您可以從網頁編輯器的工具列移除不需要的功能。

執行以下步驟，從工具列移除任何不想要的特徵：

1. 若要下載UI設定檔，請以管理員身分登入Adobe Experience Manager。

1. 按一下頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取&#x200B;**指南**，然後按一下&#x200B;**資料夾設定檔**。
1. 按一下&#x200B;**全域設定檔**&#x200B;圖磚。
1. 選取&#x200B;**XML編輯器設定**&#x200B;索引標籤，然後按一下頂端的&#x200B;**編輯**&#x200B;圖示
1. 按一下「**下載**」圖示，在本機系統上下載ui\_config.json檔案。 您可以接著對檔案進行變更，然後上傳相同的檔案。

   `ui_config.json`檔案有三個區段：

   1. **工具列**：   本節包含編輯器工具列中所有可用功能的定義，例如「插入/移除編號清單」、「\(file\)關閉」、「儲存」、「註解」等。

   1. **捷徑**：   本節包含指定給編輯器中特定功能的鍵盤快速鍵定義。

   1. **範本**：   本節包含您可在檔案中使用的DITA元素的預先定義結構。 依照預設，「範本」區段包含段落、簡單表格、表格和正文元素的範本定義。 您可以為想要的元素新增有效的XML結構，以建立任何元素的範本定義。 例如，如果您想要新增包含清單中每個新`li`元素的`p`元素，您可以在範本區段的結尾新增下列程式碼，以達成此目的：

   ```css
   "li": "<li><p></p></li>"
   ```

1. 從工具列區段中，移除您不想向使用者公開的功能專案。

1. 儲存&#x200B;*ui\_config.json*&#x200B;檔案並重新載入網頁編輯器。


**上層主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
