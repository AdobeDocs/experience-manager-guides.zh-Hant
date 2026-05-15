---
title: 整合案頭式XML編輯器
description: 瞭解如何整合案頭式XML編輯器
exl-id: 268e8613-bb3b-4577-96fb-a588dabfd834
feature: Publishing FrameMaker Documents
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/wILI1Y5nUtUiEuHG0wN4q2KCQko5mKN6CKy1Cs5kxTU
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: bf79f6d3-0ad0-4d82-99e4-42ce98324d60
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 322
ht-degree: 0%

---

# 整合案頭式XML編輯器 {#id181GB01G0HS}

市面上有許多XML編輯器，您也可能已經使用了一個。 Adobe FrameMaker是最強大的XML編輯器之一，它附帶AEM聯結器。 使用FrameMaker中的AEM聯結器，您可以輕鬆與AEM存放庫連線、取出和簽入檔案，以及直接在FrameMaker中編輯檔案。 您也可以設定Experience Manager Guides以從網頁編輯器啟動FrameMaker。 在FrameMaker中開啟檔案後，您可以編輯該檔案並將其簽回AEM存放庫。

## 從網頁編輯器在FrameMaker中啟用檔案編輯

您可以使用FrameMaker或任何其他DITA編輯器來建立和更新DITA內容。 但是，如果您的組織使用FrameMaker作為DITA編輯器，則您可以為使用者提供直接從AEM在FrameMaker中開啟DITA檔案的選項。

依預設，您的使用者在AEM工具列上看不到&#x200B;**在FrameMaker中開啟**&#x200B;按鈕。 執行以下步驟，在AEM工具列上新增此按鈕：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。
   ![](assets/open-in-fm-config.png)

1. 選取&#x200B;**在FrameMaker中顯示開啟按鈕**&#x200B;選項。

1. 如果您使用版本4.6和FrameMaker 2022 9月版 — 更新3，您必須啟用&#x200B;**FrameMaker版本2022更新3或以上版本**&#x200B;設定，使用者才能將Experience Manager Guides伺服器詳細資料傳遞至FrameMaker。 預設為停用。


1. 按一下&#x200B;**儲存**。


當您啟用&#x200B;**在FrameMaker中顯示開啟**&#x200B;選項時，在AEM存放庫中選取任何DITA檔案時，就會顯示&#x200B;**在FrameMaker中開啟**&#x200B;按鈕。 當此選項&#x200B;*未啟用*&#x200B;時，只有當您在存放庫中選取.fm或.book檔案時，才會顯示&#x200B;**在FrameMaker中開啟**&#x200B;按鈕。



