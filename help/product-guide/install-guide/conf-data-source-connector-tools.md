---
title: 使用工具設定資料來源聯結器
description: 瞭解如何使用工具設定資料來源聯結器。
exl-id: 2a0ac0a0-b2a9-453e-851b-fb04c8903526
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 1eb4fcb33d6f905df3f543232e7040d1da42560b
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# 從使用者介面設定資料來源聯結器

Experience Manager Guides隨附&#x200B;**資料來源**&#x200B;工具，可協助您設定資料來源的現成聯結器。 您可以為JIRA、SQL (MySQL、PostgreSQL、Microsoft SQL Server、SQLite、MariaDB、H2DB)、AdobeCommerce和Elasticsearch資料庫設定聯結器。

若要設定聯結器，請執行下列步驟：

1. 選取頂端的&#x200B;**Adobe Experience Manager**&#x200B;連結，然後選擇[工具]。
1. 從工具清單中選取&#x200B;**指南**。
1. 選取&#x200B;**資料來源**&#x200B;圖磚。 顯示&#x200B;**資料來源**&#x200B;頁面。 您可以檢視已連線的資料來源。

   您可以在&#x200B;**清單檢視**&#x200B;或&#x200B;**並排檢視**&#x200B;之間切換，以清單或並排方式檢視各種連線的資料來源。

   <img src="./assets/data-sources-create-window.png" alt= "列在資料來源頁面上的資料來源" width="800">

   *檢視或建立資料來源聯結器。*
1. 按一下&#x200B;**建立**。
1. 選取要建立聯結器的資料庫。 例如，Elasticsearch聯結器。
   >[!NOTE]
   >
   >列出所有可用的現成資料庫。

1. 按一下「**下一步**」。
1. 根據資料庫輸入組態和連線詳細資訊。

   >[!TIP]
   >* 暫留在 <img src="./assets/info-details.svg" alt= "資訊圖示" width="25">在欄位附近以檢視更多相關詳細資訊。
   > * 包含*的欄位為必填欄位。 例如，您可以為Elasticsearch聯結器輸入下列詳細資訊。

   * **名稱**：輸入資料來源的名稱。
   * 驗證型別：從下拉式清單中選取驗證型別。 例如，基本的使用者名稱 — 密碼驗證
   * **使用者名稱**：輸入您的使用者名稱。
   * **密碼**：輸入您的使用者名稱和密碼。
   * **URL**：新增API URL。

1. 選取&#x200B;**測試連線**。 在新增必要的詳細資訊後，您才能檢視已啟用的&#x200B;**測試連線**&#x200B;按鈕。 如果連線詳細資料正確，請檢視成功訊息。 否則，您可能會檢視錯誤訊息。



1. 選取頂端的&#x200B;**儲存**&#x200B;以儲存聯結器。     在您填寫所有詳細資料且連線成功後，檢視已啟用的&#x200B;**儲存**&#x200B;按鈕。


   如果聯結器儲存成功，您可以在頁面上檢視連線的資料來源。

## 聯結器可用的功能

* 在&#x200B;**清單檢視**&#x200B;或&#x200B;**並排檢視**&#x200B;之間切換，以清單或並排方式檢視各種連線的資料來源。
* 選取單一聯結器的核取方塊。 按一下「全選&#x200B;**」**&#x200B;以選取所有聯結器。 選取所有聯結器時，您可以按一下&#x200B;**取消選取全部**。

<img src="./assets/data-sources-features.png" alt= "資料來源頁面上的資料來源功能" width="800">

*編輯、重新連線、複製或刪除資料來源聯結器。*

您可以在&#x200B;**資料來源**&#x200B;頁面上為聯結器使用下列功能：

* **編輯**：編輯所選聯結器的組態詳細資料。

* **重新連線**：重新連線到中斷連線的聯結器。

* **重複**：使用目前的聯結器做為基底來建立新的重複聯結器。 根據預設，會以尾碼（如connectorname_1）建立重複的聯結器。 例如，sample-elastic-search_1。
如果同名的聯結器存在，則會檢視錯誤。

* **刪除**：刪除選取的聯結器。


設定資料來源後，聯結器會列在網頁編輯器的&#x200B;**資料來源面板**&#x200B;下。 然後，您可以連線至資料來源，並將內容片段插入主題中。 如需詳細資訊，請檢視[使用資料來源中的資料](../user-guide/web-editor-content-snippet.md)。

>[!NOTE]
>
>您也可以建立自訂聯結器，並將它們用於不同的資料來源。 瞭解如何[設定自訂聯結器](../knowledge-base/kb-articles/data-source/conf-custom-data-source-connector.md)。