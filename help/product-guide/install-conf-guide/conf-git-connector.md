---
title: 在AEM Guides中設定Git聯結器
description: 瞭解如何在Experience Manager Guides中設定Git。
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: eb30be6342a50ba52e8afd8b4a31148b3ad9c340
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 從使用者介面建立及設定Git聯結器

>[!NOTE]
>
> 此功能預設為停用。 若要啟用您的環境，請聯絡您的客戶成功團隊。

使用Experience Manager Guides中的資料來源工具，從使用者介面建立並設定Git聯結器。 成功設定聯結器後，您可使用它將Git存放庫中的內容匯入Experience Manager Guides。

>[!NOTE]
>
> 開始之前，請確定Git聯結器已部署到您的Cloud Manager專案。 如需詳細資訊，請檢視[將Git聯結器新增至您的Cloud Manager專案。](#add-git-connector-to-your-cloud-manager-project)


1. 選取頂端的&#x200B;**Adobe Experience Manager**&#x200B;連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取&#x200B;**指南**。
1. 選取&#x200B;**資料來源**&#x200B;圖磚。 顯示&#x200B;**資料來源**&#x200B;頁面。
1. 選擇 **建立**。
1. 從資料來源聯結器清單中，選取&#x200B;**GitHub**。

   ![](assets/github-connector-tile.png){width="600"}

1. 選取&#x200B;**「下一步」**。
1. 輸入組態和連線詳細資料。

   ![](assets/conf-git-connector.png){width="600"}

   >[!TIP]
   >
   >* 暫留在 <img src="./assets/info-details.svg" alt= "資訊圖示" width="25">在欄位附近以檢視更多相關詳細資訊。
   >* 包含*的欄位為必填欄位。 例如，您可以為Elasticsearch聯結器輸入下列詳細資訊。

   &#x200B;- **名稱**：輸入資料來源的名稱。
   &#x200B;- **目標AEM根路徑**：輸入應儲存從Git匯入之內容的AEM存放庫路徑。
   &#x200B;- **檔案型別篩選（包含）**：指定匯入時要包含的檔案型別。
   &#x200B;- **排除的路徑（規則運算式）**：指定要從匯入排除的路徑模式。
   &#x200B;- **驗證型別**：從下拉式清單中選取驗證型別。 目前，**個人存取權杖(PAT)**&#x200B;是唯一支援的驗證方法。 在聯結器設定期間輸入PAT以驗證和存取Git存放庫。

     瞭解如何[產生GitHub個人存取權杖](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic)。

     在GitHub產生PAT期間選取範圍時，請務必啟用下列範圍：
     &#x200B;- **repo**：選取最上層核取方塊。 會自動選取所有子範圍，授與存放庫內容、認可狀態和部署的存取權。
     &#x200B;- **管理員:org**：僅選取&#x200B;**讀取:org**。 這是解析組織和團隊成員資格所必需的。
   * **存放庫URL**：輸入應從中匯入內容的Git存放庫URL。
   * **分支**：輸入用於內容匯入的分支。

1. 測試連線。 **測試連線**&#x200B;按鈕只有在您輸入必要的詳細資料之後才會啟用。 如果連線詳細資料正確，則會顯示成功訊息。 否則，會出現錯誤訊息。

   ![](assets/git-connector-test-connection.png){width="600"}

1. 選取頂端的&#x200B;**儲存**&#x200B;以儲存聯結器。

   只有在輸入所有必要的詳細資料且連線成功之後，才會啟用「儲存」按鈕。 如果聯結器儲存成功，您可以在&#x200B;**資料來源**&#x200B;頁面上檢視已設定的Github聯結器。

   ![](assets/git-connector-connected.png){width="600"}

## 將Git聯結器新增至您的Cloud Manager專案

Git Connector必須先內嵌在AEM專案中，才能從&#x200B;**資料來源**&#x200B;頁面設定。 執行以下步驟來新增相依性：

1. 在您的AEM專案的`all/pom.xml`中，將Git Connector新增為`<dependencies>`下的相依性：

   ```xml
   <dependency>
       <groupId>com.adobe.aem.addon.guides</groupId>
       <artifactId>konnect-github</artifactId>
       <version>1.0.0</version>
   </dependency>
   ```

1. 在同一`pom.xml`中，將相依性新增至`filevault-package-maven-plugin`設定的`<embeddeds>`區段：

   ```xml
   <embedded>
       <groupId>com.adobe.aem.addon.guides</groupId>
       <artifactId>konnect-github</artifactId>
       <type>jar</type>
       <target>/apps/YOUR-vendor-packages/content/install</target>
   </embedded>
   ```

   將`YOUR-vendor-packages`取代為您專案的廠商套件名稱。

1. 提交變更並將其推播到您的Cloud Manager Git存放庫，然後執行管道以部署這些變更。

管道完成後，Git Connector會安裝在您的環境中，並可從&#x200B;**資料來源**&#x200B;頁面設定。





