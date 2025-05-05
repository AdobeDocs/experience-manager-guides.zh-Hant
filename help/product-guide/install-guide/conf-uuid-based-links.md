---
title: 設定UUID型連結的顯示方式
description: 瞭解如何設定顯示UUID型連結
exl-id: ab1b0ecf-cb50-4fcd-b36e-d16a8c396054
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 設定UUID型連結的顯示方式 {#id2035G20M0QN}

根據預設，當您在Web編輯器中使用「插入參照」或「插入重複使用內容」選項建立連結時，會使用參照內容的UUID來建立連結。 參考內容的&#x200B;**連結**&#x200B;屬性\（在「屬性」面板中\）可設定為顯示參考內容或UUID的相對檔案路徑。 這個顯示是由configMgr中的&#x200B;**啟用UUID**&#x200B;選項所控制。 預設會開啟，這表示參考內容的UUID會顯示在「屬性」面板中。

執行以下步驟，在網頁編輯器中顯示參照內容的相對路徑或UUID：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 在&#x200B;*XmlEditorConfig*&#x200B;設定中，**啟用UUID**&#x200B;選項預設為啟用。 這表示參考內容的UUID顯示在「屬性」面板的&#x200B;**Link**&#x200B;屬性中。

   如果要顯示連結內容的相對路徑，請取消選取&#x200B;**啟用UUID**&#x200B;選項。

1. 按一下「**儲存**」。


**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](conf-web-editor.md)
