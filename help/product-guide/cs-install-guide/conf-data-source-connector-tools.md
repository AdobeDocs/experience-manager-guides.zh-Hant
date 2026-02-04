---
title: 使用工具設定資料來源聯結器
description: 瞭解如何使用工具設定資料來源聯結器。
exl-id: d7cd412b-89ea-43a5-97b3-09944863bbee
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: c790d5edd1ab799564aebfa96f4a41288c977a6c
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# 從使用者介面設定資料來源聯結器

Experience Manager Guides隨附&#x200B;**資料來源**&#x200B;工具，可協助您設定資料來源的現成聯結器。 您可以設定JIRA、SQL (MySQL、PostgreSQL、Microsoft SQL Server、SQLite、MariaDB、H2DB)、AdobeCommerce、Elasticsearch和一般REST使用者端聯結器。


除了這些現成可用的聯結器外，Experience Manager Guides還提供Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO)資料來源的聯結器。 您可以從[Maven中央存放庫](https://central.sonatype.com/search?q=com.adobe.aem.addon.guides)下載並安裝這些開放原始碼聯結器。 接著，使用者即可設定這些聯結器。
瞭解如何[安裝開放原始碼聯結器](#install-open-source-connector)。



您也可以使用檔案聯結器來連線至JSON資料檔案。 從您的電腦上傳JSON檔案，或從Adobe Experience Manager資產瀏覽該檔案。 然後，使用產生器建立內容片段或主題。

若要設定聯結器，請執行下列步驟：

1. 選取頂端的&#x200B;**Adobe Experience Manager**&#x200B;連結，然後選擇[工具]。
1. 從工具清單中選取&#x200B;**指南**。
1. 選取&#x200B;**資料來源**&#x200B;圖磚。 顯示&#x200B;**資料來源**&#x200B;頁面。 您可以檢視已連線的資料來源。

   您可以在&#x200B;**清單檢視**&#x200B;或&#x200B;**並排檢視**&#x200B;之間切換，以清單或並排方式檢視各種連線的資料來源。

   <img src="./assets/data-sources-create-window.png" alt= "列在資料來源頁面上的資料來源" width="800">

   *檢視或建立資料來源聯結器。*

1. 按一下「**建立**」。
1. 選取要建立聯結器的資料庫。 例如Elasticsearch聯結器。

   >[!NOTE]
   >
   >列出所有可用的現成資料庫。

1. 按一下「**下一步**」。
1. 根據資料庫輸入組態和連線詳細資訊。

   >[!TIP]
   >
   >* 暫留在 <img src="./assets/info-details.svg" alt= "資訊圖示" width="25">在欄位附近以檢視更多相關詳細資訊。
   >* 包含*的欄位為必填欄位。 例如，您可以為Elasticsearch聯結器輸入下列詳細資訊。

   * **名稱**：輸入資料來源的名稱。
   * **驗證型別**：從下拉式清單中選取驗證型別。 例如，基本的使用者名稱 — 密碼驗證
   * **使用者名稱**：輸入您的使用者名稱。
   * **密碼**：輸入您的使用者名稱和密碼。
   * **URL**：新增API URL。


1. 選取&#x200B;**Exclude factory templates**&#x200B;選項，以排除工廠範本不用於產生主題和程式碼片段。 它們不會出現在&#x200B;**新增內容片段產生器**&#x200B;或&#x200B;**新增主題產生器**&#x200B;對話方塊中的&#x200B;**資料對應範本**&#x200B;下拉式清單下。
1. 選取&#x200B;**測試連線**。 在新增必要的詳細資訊後，您才能檢視已啟用的&#x200B;**測試連線**&#x200B;按鈕。 如果連線詳細資料正確，請檢視成功訊息。 否則，您可能會檢視錯誤訊息。
1. 選取頂端的&#x200B;**儲存**&#x200B;以儲存聯結器。     在您填寫所有詳細資料且連線成功後，檢視已啟用的&#x200B;**儲存**&#x200B;按鈕。


   如果聯結器儲存成功，您可以在頁面上檢視連線的資料來源。

**連線到多個資源**

您可以根據某些聯結器的不同URL新增或使用多個資源，例如通用REST使用者端、Salsify、Akeneo和Microsoft Azure DevOps面板(ADO)。 然後，與他們連結，使用產生器建立內容片段或主題。

執行以下步驟來建立資源：

1. 在![URL資源區段](assets/Add_icon.svg)中選取&#x200B;**新增圖示**，為每個URL新增資源。
1. 在&#x200B;**新增資源**&#x200B;對話方塊中設定所有詳細資料。
1. 按一下&#x200B;**新增**。
1. 您可以編輯![編輯圖示](assets/edit_pencil_icon.svg)或從URL資源清單刪除![刪除](assets/Delete_icon.svg)資源。
1. 您也可以使用Salsify、Akeneo和Microsoft ADO等資料來源可用的預設資源。 將您不想要為資料來源設定的資源選項切換為OFF。

這可協助您從單一內容片段或主題中特定資料來源的任何資源快速擷取資料。



## 安裝開放原始碼聯結器{#install-open-source-connector}

若要將[Maven中央存放庫](https://central.sonatype.com/search?q=com.adobe.aem.addon.guides)上存在的相依性發佈到雲端服務，您必須包含並內嵌開放原始碼聯結器的相依性。

1. 在您的Cloud Manager Git專案程式碼的`all/pom.xml`中新增相依性。 例如，您可以為Microsoft Azure DevOps Boards資料來源聯結器新增下列相依性。


   ```
   <dependency>
       <groupId>com.adobe.aem.addon.guides</groupId>
       <artifactId>konnect-azure-devops</artifactId>
       <version>1.0.0</version>
       <type>jar</type>
   </dependency> 
   ```

1. 內嵌新增的相依性。

   ```
   <embedded>
       <groupId>com.adobe.aem.addon.guides</groupId>
       <artifactId>konnect-azure-devops</artifactId>
       <type>jar</type>
       <target>/apps/aemdoxonaemcsstageprogram-vendor-packages/content/install</target>
   </embedded> 
   ```

1. 執行管道以套用雲端服務中的變更。
聯結器會安裝在您的環境中。


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


設定資料來源後，聯結器會列在網頁編輯器的&#x200B;**資料來源面板**&#x200B;下。 然後，您可以連線至資料來源，並將內容片段插入主題中。 如需詳細資訊，請檢視[插入資料來源的內容片段](../user-guide/web-editor-content-snippet.md)。

