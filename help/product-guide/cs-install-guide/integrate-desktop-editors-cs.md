---
title: 整合案頭式XML編輯器
description: 瞭解如何整合案頭式XML編輯器
feature: Publishing FrameMaker Documents
role: Admin
level: Experienced
exl-id: 86ba53fa-0e08-4791-9018-09fe974691da
TQID: https://experienceleague.adobe.com/4cejVcInzwcFBWgxobUvn7g2teizpQCCeTC2Z5CZ1K8
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: bf79f6d3-0ad0-4d82-99e4-42ce98324d60
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 368
ht-degree: 1%

---

# 整合案頭式XML編輯器

市面上有許多XML編輯器，您也可能已經使用了一個。 Adobe FrameMaker是最強大的XML編輯器之一，它附帶AEM聯結器。 使用FrameMaker中的AEM聯結器，您可以輕鬆與AEM存放庫連線、取出和簽入檔案，以及直接在FrameMaker中編輯檔案。 您也可以設定Experience Manager Guides以從網頁編輯器啟動FrameMaker。 在FrameMaker中開啟檔案後，您可以編輯該檔案並將其簽回AEM存放庫。

## 從網頁編輯器在FrameMaker中啟用檔案編輯

您可以使用FrameMaker或任何其他DITA編輯器來建立和更新DITA內容。 但是，如果您的組織使用FrameMaker作為DITA編輯器，則您可以為使用者提供直接從AEM在FrameMaker中開啟DITA檔案的選項。


依預設，您的使用者在AEM工具列上看不到&#x200B;**在FrameMaker中開啟**&#x200B;按鈕。 執行以下步驟，在AEM工具列上新增此按鈕：

使用[組態覆寫](download-install-additional-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以在AEM工具列上新增此按鈕：


| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.openinframebuttonshow` | 布林值\(true/false\)。 如果要顯示&#x200B;**在FrameMaker中開啟**&#x200B;按鈕，則將此屬性設定為true。<br> **預設值**： false |



如果您使用版本2409和FrameMaker 2022 9月版本 — Update 3，您必須啟用&#x200B;**FrameMaker版本2022 Update 3或以上版本**&#x200B;設定，使用者才能將Experience Manager Guides伺服器詳細資料傳遞至FrameMaker。  預設為停用。


| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.openinframe2022above` | 布林值\(true/false\)。 如果您使用的是FrameMaker 2022年9月版 — 更新3 ，則將此屬性設定為true。<br> **預設值**： false |



當您將&#x200B;*openinframebuttonshow*&#x200B;屬性設定為true時，在AEM存放庫中選取任何DITA檔案時，就會顯示&#x200B;**在FrameMaker中開啟**&#x200B;按鈕。 當此屬性未設定為&#x200B;*true*&#x200B;時，只有當您在存放庫中選取.fm或.book檔案時，才會顯示&#x200B;**在FrameMaker中開啟**&#x200B;按鈕。
