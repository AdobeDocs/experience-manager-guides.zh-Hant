---
title: Experience Manager Guides和Edge Delivery Services
description: 瞭解Edge Delivery Services如何擴展Experience Manager Guides的撰寫和發佈可能性。
feature: Output Generation
role: Admin
level: Experienced
exl-id: a4623088-a867-4079-80d6-20866c99683e
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 63ae0f947d50646bed34cd815db6b9fb585fc015
workflow-type: tm+mt
source-wordcount: '1916'
ht-degree: 1%
---
# Experience Manager Guides和Edge Delivery Services

Adobe Experience Manager Guides可讓您透過專用的GitHub型發佈設定檔，直接將DITA內容發佈至Edge Delivery Services (EDS)。 此功能可讓組織提供高效能、回應式檔案體驗，同時在Experience Manager Guides中維護DITA型撰寫工作流程。

如需在Adobe Experience Manager中使用EDS的詳細資訊，請檢視[Edge Delivery Services概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/edge-delivery/overview)。

若要啟用從Experience Manager Guides發佈至EDS的功能，您必須完成GitHub和Experience Manager Guides的一系列設定步驟。 以下各節將依序概述每個步驟，並解釋它們在整體發佈工作流程中如何搭配運作。

1. [為EDS設定並設定GitHub](#set-up-and-configure-github-for-eds)
2. [在Experience Manager Guides中為EDS建立並設定發佈設定檔](#create-and-configure-a-publish-profile-for-eds-in-experience-manager)
3. [使用EDS區塊自訂輸出](#customize-output-using-eds-blocks)

如需快速影片逐步解說，請檢視[在AEM Guides中發佈](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/knowledge-base/expert-session/publishing-in-aem-guides-aug25)。



## 為EDS設定並設定GitHub

本節說明如何設定及使用EDS的GitHub。 內容包括使用Adobe檔案集建立存放庫、透過AEM Code Sync連線GitHub至Adobe Experience Manager、設定必要的GitHub和OAuth應用程式，以及定義用於發佈內容的存放庫掛載點。

### 為EDS建立GitHub存放庫

EDS需要預先定義結構的GitHub存放庫。 Adobe提供專為Experience Manager Guides使用者設計的官方檔案存放庫。

執行以下步驟來建立您的存放庫：

1. 開啟Experience Manager Guides範本範本存放庫[aem-guides-boilerplate](https://github.com/adobe/aem-guides-boilerplate)。
   ![](assets/eds-boilerplate-template.png)

2. 使用此範本建立新的存放庫。 瞭解[從範本](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)建立存放庫。 確定存放庫可見性已設定為&#x200B;*公用*，以便EDS可以存取它。

   ![](assets/eds-create-new-repo.png)

存放庫現在已建立，並與樣版範本結構一致。

![](assets/eds-repo-created-github-view.png)

### 建立新的OAuth應用程式

在Experience Manager Guides中建立EDS發佈設定檔時，需要OAuth應用程式才能驗證使用者。 它使用&#x200B;*使用者端識別碼*&#x200B;和&#x200B;*使用者端密碼*&#x200B;來啟用安全的登入流程。

執行以下步驟來建立新的OAuth應用程式：

1. 在GitHub上，導覽至左側邊欄並選取&#x200B;**開發人員設定**。
2. 在左側邊欄中，選取&#x200B;**OAuth應用程式**。
3. 選取&#x200B;**新的OAuth應用程式**。

   ![](assets/eds-new-oauth-app.png){width="650"}

4. 提供下列必要詳細資訊，註冊您的應用程式：

   - **應用程式名稱**：輸入您的EDS存放庫名稱
   - **首頁URL**：輸入Experience Manager Guides執行個體的URL。 （如需範例URL格式，請參閱[建立新的GitHub應用程式](#create-a-new-github-app)區段的步驟4）。
   - **授權回呼URL**：與首頁URL相同

5. 選取&#x200B;**啟用裝置流程**&#x200B;選項，然後選取&#x200B;**註冊應用程式**&#x200B;以完成註冊。

   ![](assets/eds-new-github-app-register.png){width="650"}

您的應用程式現已準備就緒。 記下&#x200B;*使用者端識別碼*。 在Experience Manager Guides中設定發佈設定檔時，您現在或稍後可以產生最多5個&#x200B;*使用者端密碼*。

![](assets/eds-new-oauth-app-page.png)


### 在EDS存放庫中設定掛接點URL

EDS會從存放庫根目錄之`fstab.yaml`檔案中定義的&#x200B;*掛接點* URL讀取內容。 此URL會將EDS指向Experience Manager Guides發佈所產生內容的位置。

若要在`fstab.yaml`檔案中設定掛接點URL：

1. 在您的GitHub存放庫中，開啟`fstab.yaml`檔案。
2. 使用以下格式更新`url`值：

   ```text
   https://guides.adobe.com/eds-workers/<account type>/<git acc domain>/<git username>/<git repo>/<branch>/<root folder>
   ```

   下表說明URL中的每個欄位：

   | 欄位 | 說明 |
   |---|---|
   | `https://guides.adobe.com/eds-workers` | Experience Manager Guides用來將內容發佈至EDS的工作者URL。 請勿變更此值。 |
   | `<account type>` | Git帳戶型別。 設定為`github`。 |
   | `<git acc domain>` | Git帳戶的網域。 設定為`github.com`。 |
   | `<git username>` | 您的GitHub使用者名稱。 |
   | `<git repo>` | 您為EDS建立的GitHub存放庫名稱。 |
   | `<branch>` | 您要發佈內容的分支。 預設值為 `main`。 如果您在GitHub上變更分支名稱，請在此處並在Experience Manager Guides的EDS發佈設定檔中更新。 |
   | `<root folder>` | 已發佈檔案認可所在之存放庫的根資料夾。 預設值為 `docs`。 如果您在GitHub上變更資料夾名稱，請在此處並在Experience Manager Guides的EDS發佈設定檔中更新。 |

   例如，若您的GitHub使用者名稱為`my-username`，而存放庫名稱為`my-eds-repo`，則`fstab.yaml`檔案會顯示如下：

   ```yaml
   mountpoints:
     /:
       url: https://guides.adobe.com/eds-workers/github/github.com/my-username/my-eds-repo/main/docs
       type: markup
   ```

   ![](assets/eds-fstab-yaml-file.png){width="650"}

   >[!NOTE]
   >
   > 如果您繼續使用舊版URL格式(`https://guides.adobe.com/eds-workers/<git username>/<git repo>/<branch>/<root folder>`)，則帳戶型別和網域預設為`github`和`github.com`。

3. 透過AEM程式碼同步](#connect-github-to-adobe-via-aem-code-sync)區段從[連線GitHub至Adobe重複步驟2和3，以授權存放庫。

### 透過AEM程式碼同步連線GitHub至Adobe

Adobe Experience Manager使用名為&#x200B;**AEM Code Sync**&#x200B;的GitHub應用程式，將內容從Experience Manager Guides推送至GitHub。

執行以下步驟來安裝和設定&#x200B;*AEM Code Sync*&#x200B;應用程式：

1. 瀏覽至[AEM程式碼同步](https://github.com/apps/aem-code-sync)頁面，並選取&#x200B;**安裝**。

   **AEM Code Sync**&#x200B;會監視存放庫變更，並確保將更新正確推送至GitHub。

   >[!NOTE]
   >
   >安裝應用程式時，請確定您使用擁有存放庫的相同GitHub帳戶。

   ![](assets/eds-aem-code-sync-page.png)

2. 在下一頁，授予您所建立之存放庫的存取權。 選取&#x200B;**僅選取存放庫**，然後從下拉式清單中選取您的存放庫。

   ![](assets/eds-aem-code-sync-install-authorize.png){width="350"}

3. 選取&#x200B;**安裝並授權**。

   系統會將您重新導向至GitHub設定頁面。

   ![](./assets/aem-code-sync-source-code-github.png)

4. 檢閱原始程式碼詳細資料，並選取&#x200B;**下一步**。

5. 在&#x200B;**內容來源**&#x200B;頁面上，設定下列設定：

   - **內容來源型別：**&#x200B;選取&#x200B;**其他（使用您自己的標籤）**。
   - **內容來源URL：**&#x200B;檢閱在`fstab.yaml`檔案中設定為掛接點URL的URL。 如果您尚未更新檔案中的URL，可以在此處更新。
   - **副檔名：**&#x200B;將預設`.html`尾碼變更為`.htm`。

   請確定已選取&#x200B;**使用不同的內容來源**。

6. 在&#x200B;**使用者**&#x200B;頁面上，視需要新增使用者，然後選取&#x200B;**下一步**。

7. 檢閱組態摘要，並選取&#x200B;**儲存**。

   成功註冊後，確認頁面隨即顯示。 您可以從此頁面複製並儲存您網站的&#x200B;**預覽**&#x200B;和&#x200B;**即時** URL。

   ![](assets/eds-aem-code-sync-registered.png)

## 為EDS設定並設定GitLab

如需將GitLab設定為Edge Delivery Services的發佈存放庫的指示，請檢視[設定EDS的GitLab ](./configure-eds-gitlab.md)。

## 在Experience Manager中為EDS建立並設定發佈設定檔

以下各節將依序概述每個步驟，並說明如何在Experience Manager Guides中設定EDS發佈設定檔、設定輸出預設集及使用EDS產生輸出。

### 建立GitHub或GitLab的EDS發佈設定檔

1. 移至&#x200B;**[Workspace設定](/help/product-guide/cs-install-guide/workspace-settings.md)** **>** **發佈設定檔**。
2. 選取&#x200B;**+**&#x200B;圖示以建立新的發佈設定檔，並提供下列詳細資料：

   - **伺服器型別\*：**&#x200B;從下拉式清單中選取&#x200B;**Git （Edge Delivery服務）**。
   - **名稱\*：**&#x200B;輸入發佈設定檔的名稱。
   - **Git帳戶型別\*：**&#x200B;從下拉式清單中選取&#x200B;**GitHub**&#x200B;或&#x200B;**GitLab**，視您的Git存放庫提供者而定。
   - **執行個體URL\*：**&#x200B;輸入GitHub或GitLab執行個體的URL，例如`https://github.com`或`https://gitlab.com`。
   - **存放庫名稱\*：**&#x200B;輸入您的GitHub或GitLab存放庫名稱。
   - **使用者名稱\*：**&#x200B;請輸入您的GitHub或GitLab使用者名稱。
   - **分支名稱：**&#x200B;設定為`main` （預設）。
   - **根資料夾\*：**&#x200B;設定為`docs` （預設）。
   - **網站擁有者（*僅限GitLab*）：**&#x200B;輸入Edge Delivery Services網站的擁有者。
   - **網站存放庫（*僅限GitLab*）：**&#x200B;請輸入與Edge Delivery Services網站關聯的存放庫名稱。
   - **HLX API金鑰：**&#x200B;輸入您EDS組態的HLX API金鑰。 若要支援2026.11.0版Experience Manager Guides as a Cloud Service中推出的未發佈功能，此金鑰為必要專案。 此外，如果內容大小超過100個檔案，則需要金鑰才能將內容發佈到EDS。
   - **驗證認證：**&#x200B;根據選取的Git帳戶型別提供認證：
     - **GitHub：**&#x200B;輸入從您的GitHub OAuth應用程式取得的&#x200B;**使用者端識別碼\***和&#x200B;**使用者端密碼\***。 如需詳細資訊，請參閱[建立新的OAuth應用程式](#create-a-new-oauth-app)。
     - **GitLab：**&#x200B;請輸入為您的GitLab帳戶產生的&#x200B;**Access Token\***。
3. （*僅限GitHub*）選取&#x200B;**登入**&#x200B;以進行驗證。 對於GitLab，不需要登入，因為存取權杖是用於驗證。

   ![](assets/eds-publish-profile.png){width="650"}

4. 選取「**儲存**」。 對於GitHub，在成功驗證後，**儲存**&#x200B;選項即可使用。

現在已設定您的EDS發佈設定檔。

### 建立EDS的輸出預設集並產生輸出

1. 在Map主控台中開啟地圖。
2. 在&#x200B;**輸出預設集**&#x200B;索引標籤中，選取&#x200B;**+**&#x200B;以建立新的輸出預設集。
3. 在&#x200B;**新輸出預設集**&#x200B;對話方塊中，提供下列詳細資料：
   - **型別**：選取&#x200B;**Edge Delivery服務**
   - **名稱**：提供此預設集的名稱
4. 選取「**新增**」。

   ![](assets/eds-output-preset.png){width="650"}
5. 開啟新建立的EDS輸出預設集，並設定下列欄位：

   - **條件式篩選：**&#x200B;選取&#x200B;**無**&#x200B;產生輸出而不進行篩選，或選取&#x200B;**使用DITAVAL**&#x200B;套用條件式篩選。
   - **發佈子資料夾：**&#x200B;輸入發佈輸出的子資料夾名稱。 子資料夾會建立於根資料夾下的存放庫中，其名稱會出現在已發佈內容的EDS連結中。 例如，如果根資料夾為`docs`，而發佈子資料夾為`product-guide`，則內容會發佈至`docs/contents/product-guide`。
   - **發佈設定檔：**&#x200B;選取在上一節中設定的GitHub或GitLab發佈設定檔。

     ![](assets/eds-output-preset-config.png){width="650"}

6. 選取&#x200B;**儲存**，然後選取&#x200B;**產生輸出**。

>[!NOTE]
>
>產生的輸出儲存在EDS存放庫的`<root folder>/contents/<publish subfolder>`資料夾中。

現在會產生EDS輸出。 內容以乾淨、回應式的版面配置呈現。 其中包含一般元素，例如頁面標題、階層連結、內文內容，以及主題中使用的任何區塊。 左側的目錄（從地圖產生）可協助您跨主題導覽，而右側的迷你目錄會反白標示目前頁面中的區段。 整個輸出可完全回應，確保裝置間的最佳化且一致讀取體驗。

>[!NOTE]
>
> 您可以將多個DITA map發佈到相同的網站。 發佈的地圖會顯示在左側導覽面板中，可讓使用者存取每個地圖的內容。 發佈新地圖不會覆寫先前發佈的地圖。

![](assets/eds-site-output.png)

## 使用EDS區塊自訂輸出

EDS使用`blocks`來控制內容的不同部分的樣式和顯示方式。 您可以修改現有區塊或建立自訂區塊。

以下列出的範例會逐步引導您自訂現有區塊並建立新區塊，以便在Experience Manager Guides中設定最終EDS輸出的樣式。

### 自訂階層連結區塊以更新其文字顏色

跨頁面使用階層連結，以協助使用者瞭解自己在檔案中的位置。 由於此區塊在整個網站中會一致顯示，因此更新其樣式可允許統一設計更新。

執行以下步驟來自訂階層連結區塊，以更新其文字顏色：

1. 前往您的GitHub存放庫並開啟`blocks`資料夾。
2. 選取&#x200B;**階層連結**&#x200B;區塊。

   ![](assets/eds-breadcrumbs.png){width="650"}
3. 開啟`css`檔案並更新文字色彩。
4. 將變更提交至GitHub。
5. 重新整理已上線的網站以檢視更新。

### 更新EDS指令碼以在發佈的輸出中建立自訂元素

某些情況下，您可能只想要設定內容特定部分的樣式。 請執行以下步驟，使用自訂區塊來達成此目的。

1. 開啟主題檔案並選取標籤元素內的文字。

   在下列熒幕擷圖中，已選取`example`標籤內的內容。
   ![](assets/eds-example-tag-org-output.png){width="650"}
2. 若要設定`example`標籤內的文字：
   - 瀏覽至&#x200B;**內容屬性**。
   - 新增`outputclass`屬性。
   - 將其值設為`example eds-force-block`。
   - 選取「**新增**」。
     ![](assets/eds-example-tag.png){width="650"}
3. 儲存並重新產生輸出。
4. 在`blocks`目錄中建立與`outputclass`同名的新資料夾。 瞭解[新增檔案到存放庫](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository#adding-a-file-to-a-repository-using-the-command-line)。

   ![](assets/eds-example-folder.png){width="650"}

5. 新增必要的`css`和選用的`js`檔案。

   ![](assets/eds-example-folder-subfolders.png){width="650"}

6. 認可變更並重新產生輸出。

選取的內容現在會顯示區塊中定義的自訂樣式。

![](assets/eds-example-output.png){width="650"}
