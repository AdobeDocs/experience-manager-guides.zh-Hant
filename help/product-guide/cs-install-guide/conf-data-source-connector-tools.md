---
title: 使用工具設定資料來源聯結器
description: 瞭解如何使用工具設定資料來源聯結器。
exl-id: d7cd412b-89ea-43a5-97b3-09944863bbee
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# 從使用者介面設定資料來源聯結器

Experience Manager指南隨附於 **資料來源** 可協助您為資料來源設定現成可用聯結器的工具。 您可以設定JIRA、SQL (MySQL、PostgreSQL、Microsoft SQL Server、SQLite、MariaDB、H2DB)、AdobeCommerce、Elasticsearch和一般REST使用者端聯結器。

若要設定聯結器，請執行下列步驟：

1. 選取 **Adobe Experience Manager** 在頂端連結，然後選擇「工具」。
1. 選取 **指南** 工具清單中。
1. 選取 **資料來源** 圖磚。 此 **資料來源** 頁面隨即顯示。 您可以檢視已連線的資料來源。

   您可以切換 **清單檢視** 或 **平鋪檢視** 以清單或圖磚的形式檢視各種連線的資料來源。

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
   >* 暫留在 <img src="./assets/info-details.svg" alt= "資訊圖示" width="25"> 接近欄位可檢視其詳細資訊。
   > * 包含*的欄位為必填欄位。 例如，您可以為Elasticsearch聯結器輸入下列詳細資訊。

   * **名稱**：輸入資料來源的名稱。
   * 驗證型別：從下拉式清單中選取驗證型別。 例如，基本的使用者名稱 — 密碼驗證
   * **使用者名稱**：輸入您的使用者名稱。
   * **密碼**：輸入您的使用者名稱和密碼。
   * **URL**：新增API URL。

1. 選取 **測試連線**. 您可以檢視 **測試連線** 按鈕只會在您新增必要的詳細資料後啟用。 如果連線詳細資料正確，請檢視成功訊息。 否則，您可能會檢視錯誤訊息。



1. 選取 **儲存** 以儲存聯結器。     檢視 **儲存** 按鈕會在您填寫所有詳細資料且連線成功後啟用。


   如果聯結器儲存成功，您可以在頁面上檢視連線的資料來源。

## 聯結器可用的功能

* 在 **清單檢視** 或 **平鋪檢視**  以清單或圖磚的形式檢視各種連線的資料來源。
* 選取單一聯結器的核取方塊。 按一下 **全選** 以選取所有聯結器。 您可以按一下 **取消全選** 選取所有聯結器時。

<img src="./assets/data-sources-features.png" alt= "資料來源頁面上的資料來源功能" width="800">

*編輯、重新連線、複製或刪除資料來源聯結器。*

您可以對上的聯結器使用下列功能 **資料來源** 頁面：

* **編輯**：編輯所選聯結器的設定詳細資料。

* **重新連線**：重新連線到已中斷連線的聯結器。

* **複製**：以目前的聯結器為基礎建立新的重複聯結器。 根據預設，會以尾碼（如connectorname_1）建立重複的聯結器。 例如，sample-elastic-search_1。
如果同名的聯結器存在，則會檢視錯誤。

* **刪除**：刪除選取的聯結器。


設定資料來源後，聯結器會列在 **資料來源面板** 在Web編輯器中。 然後，您可以連線至資料來源，並將內容片段插入主題中。 如需詳細資訊，請檢視 [從您的資料來源插入內容片段](../user-guide/web-editor-content-snippet.md).
