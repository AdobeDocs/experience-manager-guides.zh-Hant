---
title: 在Experience Manager Guides中設定Adobe Workfront
description: 瞭解如何在Experience Manager Guides中設定Workfront
feature: Authoring
role: Admin
level: Experienced
exl-id: 1f72642c-e694-47cd-9182-f4f4aaf69655
TQID: https://experienceleague.adobe.com/Yua4Y6xsnec3O-hpTNhSmK4HvsCwaGYbLTxUxEeQAKY
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
  - id: ae478996-b206-4712-9b0c-dc78a2644453
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: f7774ebe-aec9-42b6-97e4-5002acdc712e
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 600
ht-degree: 2%

---

# 設定Adobe Workfront

Adobe Workfront是雲端型工作管理解決方案，可協助團隊和組織有效規劃、追蹤及管理其工作。 Experience Manager Guides與Adobe Workfront的整合可讓您在Experience Manager Guides核心CCMS功能之上存取強大的專案管理功能，讓您有效率地規劃、分配和追蹤工作。

進一步瞭解Experience Manager Guides中的[Adobe Workfront整合](../user-guide/workfront-integration.md)。

## 先決條件

開始之前，請確定：

1. 您擁有Adobe Workfront的標準存取權和Experience Manager Guides的管理員存取權。
2. 您[在Adobe Workfront中建立新的自訂表單](https://experienceleague.adobe.com/zh-hant/docs/workfront/using/administration-and-setup/customize/custom-forms/design-a-form/design-a-form)，此自訂表單是Experience Manager Guides所需，請特別使用以下欄位：

   | 欄位型別 | 標籤 | 名稱 | 選擇（啟用顯示值） |
   |------------|------|------|-------------------------------|
   | 單選下拉式清單 | 任務類型 | task-type | 製作（值= AUTHOR）、發佈（值= PUBLISH）、翻譯（值= TRANSLATION）、評論（值= REVIEW） |
   | 單選下拉式清單 | 任務狀態 | task-state | 製作（值= AUTHOR）、發佈（值= PUBLISH）、翻譯（值= TRANSLATION）、評論（值= REVIEW） |
   | 含格式的文字 | 作者清單 | author-list | - |
   | 含格式的文字 | 檢閱者清單 | 檢閱者清單 | - |
   | 單行文字 | 檢閱URL | review-url | - |
   | 單行文字 | 任務URL | task-url | - |
   | 單行文字 | 電子郵件主旨 | email-subject | - |

>[!NOTE]
>
> * 在上表中，選項代表&#x200B;**工作型別**&#x200B;欄位下的可用選項。 您必須為每個選項提供&#x200B;**工作名稱**&#x200B;和&#x200B;**工作值**。 每個任務型別的名稱和值必須與上表中所述完全相同。 例如，對於工作型別Author，提供&#x200B;**Authoring**&#x200B;作為名稱，提供&#x200B;**AUTHOR**&#x200B;作為其對應值。
> * 使用內部部署服務時，請務必在&#x200B;**Day CQ Link Externalizer**&#x200B;設定中將`localhost`取代為正確的伺服器位址，以便在電子郵件通知中正確接收已解析的工作連結。
> * 在Workfront中建立稽核任務時，使用者（作者或稽核者）必須是&#x200B;**工作流程 — 使用者**&#x200B;群組的一部分。 此外，身為&#x200B;**作者**，您必須是&#x200B;**內容作者**&#x200B;及&#x200B;**作者**&#x200B;群組的成員，而身為&#x200B;**檢閱者**，您必須是&#x200B;**檢閱者**&#x200B;群組的成員。


## 快速入門

執行以下步驟，在Experience Manager Guides中設定Adobe Workfront。

1. 開啟&#x200B;**工具面板**&#x200B;並選取&#x200B;**參考線**。
2. 選取&#x200B;**設定Workfront**。

   顯示&#x200B;**Workfront設定**&#x200B;頁面。

   ![](assets/configure-workfront-page.png)

3. 在&#x200B;**Workfront設定**&#x200B;頁面上，輸入您組織的Workfront網域的完整URL、使用者端ID和使用者端密碼金鑰。

   若要存取在您的Adobe Workfront設定中設定的&#x200B;**使用者端識別碼**&#x200B;和&#x200B;**使用者端密碼**&#x200B;金鑰，請瀏覽至`Setup >> Systems>> oAuth2 Applications`。

   如需有關設定Adobe Workfront網域的詳細資訊，請在[為Workfront整合建立OAuth2應用程式](https://experienceleague.adobe.com/zh-hant/docs/workfront/using/administration-and-setup/configure-integrations/create-oauth-application#create-an-oauth2-application-using-user-credentials-authorization-code-flow)中檢視「授權代碼流程」區段。

4. 選取&#x200B;**登入並驗證**。

   系統會將您重新導向至Adobe Workfront登入頁面。
5. 使用您的Adobe Workfront電子郵件地址登入，然後選取&#x200B;**允許存取**，讓Oauth2應用程式存取您個別的Adobe Workfront帳戶。

   系統會自動將您重新導向至Experience Manager Guides上的Workfront設定頁面。

6. 在自訂表單下拉式清單中，選取您為Experience Manager Guides建立的Adobe Workfront自訂表單。 檢視[必要條件](#prerequisites)。
7. 選取&#x200B;**儲存並關閉**&#x200B;以套用並儲存Workfront組態變更。

設定之後，[使用使用者在Experience Manager Guides中擁有的相同電子郵件地址，將使用者新增至Adobe Workfront](https://experienceleague.adobe.com/zh-hant/docs/workfront/using/administration-and-setup/add-users/create-manage-users/add-users)。
