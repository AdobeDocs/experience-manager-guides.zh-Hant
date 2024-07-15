---
title: 設定關閉時簽入檔案的提示
description: 瞭解如何設定關閉時簽入檔案的提示
exl-id: d184c97f-8405-4bcd-963d-635f17584897
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 1%

---

# 設定關閉時簽入檔案的提示 {#id222HC040PE8}

當使用者嘗試使用檔案索引標籤上的&#x200B;**關閉**&#x200B;按鈕或「選項」功能表中的&#x200B;**關閉**&#x200B;選項關閉在Web編輯器中開啟的檔案時，如果檔案有未儲存的資料或未儲存的版本，則會出現一個對話方塊。 如果檔案已鎖定，系統會提示使用者解除鎖定。

預設不會啟用&#x200B;**解除鎖定檔案**&#x200B;核取方塊，您必須從configMgr啟用此核取方塊。 執行以下步驟，在Web編輯器中啟用預設選項：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 選取&#x200B;**關閉時要求籤入**&#x200B;選項。

1. 按一下「**儲存**」。


啟用此組態時，對話方塊中預設會選取&#x200B;**解除鎖定檔案**&#x200B;核取方塊。

如需詳細資訊，請參閱「使用Adobe Experience Manager Guides」as a Cloud Service指南中的&#x200B;*檔案關閉和儲存案例*&#x200B;一節。

**上層主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
