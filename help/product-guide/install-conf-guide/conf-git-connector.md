---
title: 在AEM Guides中設定Git聯結器
description: 瞭解如何在Experience Manager Guides中設定Git。
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 5f626c210e74c6d11e2441f719cfbfeb33bf55c5
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---

# 從使用者介面建立及設定Git聯結器

使用Experience Manager Guides中的資料來源工具，從使用者介面建立並設定Git聯結器。 成功設定聯結器後，您可使用它將Git存放庫中的內容匯入Experience Manager Guides。


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

   * **名稱**：輸入資料來源的名稱。
   * **目標AEM根路徑**：輸入應儲存從Git匯入之內容的AEM存放庫路徑。
   * **檔案型別篩選（包含）**：指定匯入時要包含的檔案型別。
   * **排除的路徑（規則運算式）**：指定要從匯入排除的路徑模式。
   * **驗證型別**：從下拉式清單中選取驗證型別。 目前，**個人存取權杖(PAT)**&#x200B;是唯一支援的驗證方法。 在聯結器設定期間輸入PAT以驗證和存取Git存放庫。
   * **存放庫URL**：輸入應從中匯入內容的Git存放庫URL。
   * **分支**：輸入用於內容匯入的分支。

1. 測試連線。 **測試連線**&#x200B;按鈕只有在您輸入必要的詳細資料之後才會啟用。 如果連線詳細資料正確，則會顯示成功訊息。 否則，會出現錯誤訊息。

   ![](assets/git-connector-test-connection.png){width="600"}

1. 選取頂端的&#x200B;**儲存**&#x200B;以儲存聯結器。

   只有在輸入所有必要的詳細資料且連線成功之後，才會啟用「儲存」按鈕。 如果聯結器儲存成功，您可以在&#x200B;**資料來源**&#x200B;頁面上檢視已設定的Github聯結器。

   ![](assets/git-connector-connected.png){width="600"}

