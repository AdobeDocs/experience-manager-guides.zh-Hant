---
title: 在Experience Manager Guides中設定Adobe Workfront
description: 瞭解如何在Experience Manager Guides中設定Workfront
feature: Authoring
role: Admin
level: Experienced
source-git-commit: 2748ecee0963028be5d9220f852f4dfbc122d4a0
workflow-type: tm+mt
source-wordcount: '435'
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
   | 單選下拉式清單 | 任務狀態 | task-state | 製作（值= AUTHOR）、評論（值= REVIEW） |
   | 含格式的文字 | 作者清單 | author-list | - |
   | 含格式的文字 | 檢閱者清單 | 檢閱者清單 | - |
   | 單行文字 | 檢閱URL | review-url | - |

>[!NOTE]
>
> 在上表中，選項代表&#x200B;**工作型別**&#x200B;欄位下的可用選項。 您必須為每個選項提供&#x200B;**工作名稱**&#x200B;和&#x200B;**工作值**。 每個任務型別的名稱和值必須與上表中所述完全相同。 例如，對於工作型別Author，提供&#x200B;**Authoring**&#x200B;作為名稱，提供&#x200B;**AUTHOR**&#x200B;作為其對應值。

## 開始

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



