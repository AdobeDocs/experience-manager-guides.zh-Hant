---
title: 下載並安裝雲端服務的AEM Sites範本
description: 瞭解如何下載並安裝雲端服務的AEM Sites範本
feature: Installation
role: Admin
level: Experienced
source-git-commit: 1cec8975e8aad56184793a023d066aa467d8cec5
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 1%

---

# 下載及安裝AEM Sites範本（雲端服務）

本指南提供逐步指示，說明如何設定並設定最新的AEM Guides範本，以在雲端環境中產生AEM Sites頁面。 請依照下列步驟安裝所需的套件、建立和設定預設集，以及產生AEM Sites。

## 先決條件

繼續安裝之前，請先確定符合下列必要條件：

- **Adobe Experience Manager (AEM) Cloud**： **AEM as a Cloud Service**&#x200B;的執行中執行個體具有&#x200B;**AEM Guides 2502或更新版本**。

- **必要的許可權**：您必須擁有下列許可權：

   - 存取&#x200B;**Cloud Manager**&#x200B;以部署套件。
   - 存取與您的環境相關聯的&#x200B;**Git存放庫**。
   - 在AEM Guides中建立和修改預設集的許可權。

- **下載套件**：從軟體發佈入口網站下載下列套件：

   - 元件套件： guides-components.all-1.x.0.zip
   - 網站範本： aemg-docs-1.x.0.zip

## 透過雲端部署安裝套件

安裝&#x200B;**元件套件(guides-components.all-1.x.x.zip)**&#x200B;並執行下列步驟

1. **複製Git存放庫：**
   1. 導覽至Cloud Manager左側面板中的&#x200B;**存放庫**。
   2. 選取&#x200B;**存取存放庫資訊**&#x200B;並複製Git Clone命令。

      ![選取存取存放庫資訊](/help/product-guide/knowledge-base/kb-articles/assets/publishing/access-repo.png){width="350" align="left"}

   3. 使用提供的使用者名稱和密碼將存放庫複製到本機系統（必要時產生密碼）。
2. **將套件新增至Maven套件組合：**
   1. 在您的本機複製存放庫中，建立新的Maven套件組合或新增到現有的套件組合中。
   2. 確認Maven專案中存在/jcr_root/apps/fmdita/install結構。

      ![Maven專案中的結構](/help/product-guide/knowledge-base/kb-articles/assets/publishing/maven-structure.png){width="650" align="left"}


   3. 將下載的guides-components.all-1.x.x.zip檔案放入安裝資料夾中。

3. **更新篩選器.xml：**

   1. 開啟位於父內容目錄META-INF資料夾中的filters.xml檔案。
   2. 新增下列篩選器：filter root=&quot;/apps/fmdita&quot; mode=&quot;merge&quot;/


      ![新增篩選器](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-filter-xml.png){width="650" align="left"}


4. **設定pom.xml：**&#x200B;根據您的環境需求更新pom.xml檔案。
5. **推送變更並執行管道：**
   1. 將變更推送至主要Git存放庫。
   2. 導覽至Cloud Manager中的&#x200B;**管道**，然後針對所需的環境執行管道。
6. **確認安裝：**&#x200B;部署完成後，元件套件將會安裝在AEM Cloud環境中。

## 使用已安裝的範本建立網站

1. **匯入網站範本：**
   1. 前往AEM Sites頁面(servername/sites.html/content)。
   2. 從範本中選取&#x200B;**建立** > **網站**。
   3. 使用&#x200B;**匯入**&#x200B;選項匯入網站範本aemg-docs-1.x.x.zip。
2. **選取範本：**&#x200B;選取&#x200B;**AEMG Docs 1.x.x**，然後選取&#x200B;**下一步**。
3. **輸入網站詳細資料：**&#x200B;輸入&#x200B;**網站標題**&#x200B;和&#x200B;**網站名稱**。

   ![建立網站](/help/product-guide/knowledge-base/kb-articles/assets/publishing/create-site.png){width="350" align="left"}

4. 選取「**建立**」。

## 建立AEM網站預設集

1. **建立新的預設集：**
   1. 在AEM Guides中開啟DITA map並導覽至&#x200B;**輸出**&#x200B;面板。
   2. 選取&#x200B;**建立預設集**。
   3. 選取型別為&#x200B;**AEM Sites**。
   4. 輸入預設集名稱。
   5. 取消勾選&#x200B;**使用舊版元件對應**&#x200B;設定。

      ![建立新的AEM網站預設集](/help/product-guide/knowledge-base/kb-articles/assets/publishing/create-new-output-preset.png){width="350" align="left"}

   6. 選取&#x200B;**新增**&#x200B;以建立預設集。
2. **設定AEM網站預設集：**&#x200B;有兩個選項可設定現成可用的網站(OOTB)：

   **選項1：使用網站下拉式清單**

   1. 選取&#x200B;**網站**&#x200B;作為上面建立的網站（例如AEMG檔案網站）。
   2. 驗證&#x200B;**發佈路徑**&#x200B;和&#x200B;**主題頁面**&#x200B;範本是否自動設定為：
      - 發佈路徑： /content/AEMG-Docs-Site/en/docs/product
      - 主題頁面範本：主題頁面

      ![使用網站下拉式清單來設定AEM網站](/help/product-guide/knowledge-base/kb-articles/assets/publishing/use-site-dropdown-cs.png){width="350" align="left"}

   **選項2：使用網站路徑**

   1. 手動將&#x200B;**網站路徑**&#x200B;設定為/content/AEMG-Docs-Site/en/docs/product。
   2. 確認&#x200B;**主題頁面**&#x200B;範本已自動設定為主題頁面。

      ![使用網站路徑設定AEM網站](/help/product-guide/knowledge-base/kb-articles/assets/publishing/use-site-path-cs.png){width="650" align="left"}

3. **儲存預設集：**&#x200B;儲存對預設集所做的變更。

## 產生AEM Sites

1. **產生網站：**
   1. 設定預設集後，為對應的DITA map產生AEM網站。
   2. 產生的網站將可在以下路徑取得：/content/AEMG-Docs-Site/en/docs/product。
2. **變更預設產生路徑（選用）：**&#x200B;若要變更網站產生的預設路徑，請執行下列步驟：
   1. 導覽至&#x200B;**AEM Sites**。
   2. 在OOTB網站結構下建立新產品頁面。
   3. 導覽至&#x200B;**AEMG檔案** > **英文** > **檔案**。

      ![建立頁面](/help/product-guide/knowledge-base/kb-articles/assets/publishing/create-page-cs.png){width="650" align="left"}

   4. 選取&#x200B;**首頁**&#x200B;圖磚，然後選取&#x200B;**下一步**。

      ![選取主圖磚](/help/product-guide/knowledge-base/kb-articles/assets/publishing/home-tile-cs.png){width="650" align="left"}

   5. 輸入頁面的&#x200B;**標題**&#x200B;和&#x200B;**名稱**。
   6. 選取「**建立**」。

>[!NOTE]
>
> 在部署到生產環境之前，請確定所有設定都在非生產環境中進行測試。 <br><br>如需詳細資訊，請參閱正式[部署至AEM as a Cloud Service檔案](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/implementing/deploying/overview)。
