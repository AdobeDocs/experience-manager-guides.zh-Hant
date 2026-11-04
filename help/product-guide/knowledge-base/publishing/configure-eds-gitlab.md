---
title: 設定適用於Edge Delivery Services的GitLab
description: 瞭解如何設定GitLab存放庫、存取權杖、Cloud Manager、Webhook，以及自備Git，將內容從Experience Manager Guides發佈到Edge Delivery Services。
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 380089cbcfc56b23a9cb494d49c0e39e1813eabd
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 3%
---

# 設定適用於Edge Delivery Services的GitLab

若要使用GitLab將內容從Experience Manager Guides發佈到Edge Delivery Services (EDS)，您可以透過Cloud Manager的&#x200B;*自攜Git* (BYOG)功能將GitLab存放庫連結到您的EDS網站。 本文列出循序步驟。 如需每個步驟的詳細資訊，請遵循連結的檔案。

## 運作方式

- **GitHub存放庫**&#x200B;會透過AEM Code Sync應用程式建立EDS網站。
- **GitLab存放庫**&#x200B;會儲存從Experience Manager Guides發佈的內容。
- **Cloud Manager**&#x200B;接收GitLab推播事件(webhook)並將它們同步至EDS網站，以連結這兩者。

## 先決條件

- 存取GitHub和GitLab （GitLab.com或自行託管）以建立存放庫和Token。
- 使用Cloud Manager的存取權，該角色可允許新增存放庫（部署管理員或企業所有者）。
- 在您的Adobe組織中建立整合Cloud Manager API的系統管理員或API開發人員角色。
- 已在組態服務中註冊的`aem.live`組織。 深入瞭解[組態服務設定](https://www.aem.live/docs/config-service-setup)。

## 設定Edge Delivery Services的GitLab

若要設定GitLab以搭配Edge Delivery Services使用，請依照指定順序執行下列步驟，以確保正確設定和整合。

### &#x200B;1. 使用GitHub建立EDS網站

從AEM Guides範本建立GitHub存放庫，並在其上安裝AEM程式碼同步應用程式。 儲存產生的&#x200B;**即時URL** (`https://<branch>--<github-repo>--<github-username>.aem.live`)以供稍後使用。

如需相關步驟，請檢視[建立EDS的GitHub存放庫](./configure-eds.md#create-a-github-repository-for-eds)以及[透過AEM Code Sync將GitHub連線至Adobe](./configure-eds.md#connect-github-to-adobe-via-aem-code-sync)。

>[!IMPORTANT]
>
> 請勿在Cloud Manager中使用按一下選項來建立EDS網站。 以此方式建立的網站不會為您提供後續步驟所需的管理員許可權。 進一步瞭解[準備您的Edge Delivery Services網站](https://www.aem.live/developer/byo-git#1.-prepare-your-edge-delivery-services-site)。

### &#x200B;2. 建立GitLab存放庫

從相同的AEM Guides範本建立個別的GitLab存放庫（例如`my-eds-gitlab`）。 Experience Manager Guides會將產生的輸出發佈到此存放庫。 EDS需要`main`分支。

若要建立存放庫，請建立空白專案並將[aem-guides-boilerplate](https://github.com/adobe/aem-guides-boilerplate)的內容推入其中，或將範本匯入新的專案。 如需相關步驟，請在GitLab檔案中檢視[建立專案](https://docs.gitlab.com/user/project/)和[將專案從GitHub匯入至GitLab](https://docs.gitlab.com/user/project/import/github/)。

### &#x200B;3. 設定掛接點URL

在GitHub存放庫中，更新`fstab.yaml`，讓內容來源指向GitLab存放庫，並將變更提交至`main`。

```text
https://<worker URL>/gitlab/<git acc domain>/<git username>/<git repo>/main/docs
```

| 參數 | 說明 |
|---|---|
| `<worker URL>` | Adobe提供的背景工作節點URL。 |
| `<git acc domain>` | GitLab網域（例如`gitlab.com`）或您的自行託管網域。 |
| `<git username>` | 您的GitLab使用者名稱。 |
| `<git repo>` | GitLab存放庫的名稱。 |
| `main` / `docs` | 分支和根資料夾。 Experience Manager Guides的預設值。 |

### &#x200B;4. 建立GitLab存取權杖

建立下列專案所需的存取權杖：

- **Cloud Manager**，驗證並存取存放庫。 深入瞭解[在Cloud Manager中新增外部存放庫](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/managing-code/external-repositories)。
- **Experience Manager Guides發佈設定檔**，以認可已發佈的輸出。 建立具有&#x200B;**開發人員**&#x200B;角色和`api`範圍的GitLab專案存取權杖。 在[GitLab檔案](https://docs.gitlab.com/ee/user/project/settings/project_access_tokens.html)中進一步瞭解。

>[!NOTE]
>
> 在權杖到期前續約。 如果發佈設定檔中的Token已過期，發佈作業就會失敗。 若要更新Cloud Manager使用的權杖，請檢視[管理外部存放庫的存取權杖](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/managing-code/manage-access-tokens)。

### &#x200B;5. 將GitLab存放庫新增至Cloud Manager

在Cloud Manager中，移至&#x200B;**存放庫** > **新增存放庫**，選取&#x200B;**私人存放庫**，並使用存取權杖驗證所有權。 等到存放庫狀態為&#x200B;**就緒**。 BYOG選項只有在至少一個外部存放庫準備就緒後才能使用。

如需相關步驟，請檢視[在Cloud Manager中新增外部存放庫](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/managing-code/external-repositories)。

### &#x200B;6. 產生Cloud Manager API金鑰

在Adobe Developer Console中建立API整合（**Cloud Manager** API，**OAuth伺服器對伺服器**），並複製&#x200B;**使用者端ID （API金鑰）**。

如需步驟，請檢視[建立API整合專案](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration)。

### &#x200B;7. 設定GitLab webhook

在Cloud Manager中，選取存放庫的&#x200B;**設定Webhook**，並複製&#x200B;**Webhook URL**&#x200B;和&#x200B;**密碼**。 將API金鑰附加至URL (`<webhook URL>&api-key=<CLIENT_ID>`)。 在GitLab中，移至&#x200B;**設定** > **Webhooks**、新增URL和密碼、選取`main`分支並啟用&#x200B;**推播事件**。

如需詳細資訊，請檢視[在Cloud Manager中設定外部存放庫](https://www.aem.live/developer/byo-git#2.-configure-your-external-repository-in-cloud-manager)。

### &#x200B;8. 將EDS網站新增至Cloud Manager

在Cloud Manager中，前往&#x200B;**Edge Delivery** > **新增Edge Delivery網站**，然後輸入步驟1中儲存的即時URL。 完成所有權驗證。

如需步驟，請檢視[新增Edge Delivery網站](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/edge-delivery-sites/add-edge-delivery-site)。

### &#x200B;9. 使用自備Git連線存放庫

在Cloud Manager的EDS網站上，選取&#x200B;**自攜Git (BYOG)**，選擇GitLab存放庫，然後確認。 複製並安全地儲存產生的機密。 此密碼只會顯示一次，如果您重新設定網站，則會產生新的密碼。

如需詳細資訊，請檢視[在Cloud Manager中設定您的Edge Delivery網站](https://www.aem.live/developer/byo-git#3.-configure-your-edge-delivery-site-in-cloud-manager)。

### &#x200B;10. 設定EDS網站以使用Cloud Manager

使用webhook URL中的&#x200B;**方案ID** (`/program/<PROGRAM_ID>/`)和&#x200B;**存放庫ID** (`/repo/<REPO_ID>/`)，將EDS網站的程式碼來源設定為Cloud Manager存放庫。 然後，使用步驟9中的密碼建立名為`cm-byog`的密碼。

針對管理員API呼叫，檢視[設定您的AEM網站以使用Cloud Manager](https://www.aem.live/developer/byo-git#4.-configure-your-aem-site-to-use-cloud-manager)。

### &#x200B;11. 同步和驗證

在Cloud Manager中，從網站功能表選取&#x200B;**同步程式碼**，然後選擇`main`分支。 然後開啟`https://main--<site>--<org>.aem.page`以驗證網站。

如需詳細資訊，請檢視[觸發您的第一次同步](https://www.aem.live/developer/byo-git#5.-trigger-your-first-sync)和[驗證您的AEM網站](https://www.aem.live/developer/byo-git#6.-verify-your-aem-site)。

### &#x200B;12. 從Experience Manager Guides發佈

使用步驟4中的專案存取權杖，建立&#x200B;**Git帳戶型別**&#x200B;設為&#x200B;**GitLab**&#x200B;的EDS發佈設定檔。 然後在EDS輸出預設集中選取此設定檔並產生輸出。 輸出已提交到GitLab存放庫的`docs`資料夾。

如需步驟，請檢視[建立EDS發佈設定檔](./configure-eds.md#create-the-eds-publish-profile-for-github-or-gitlab)和[建立EDS的輸出預設集並產生輸出](./configure-eds.md#create-an-output-preset-for-eds-and-generate-output)。

## 疑難排解

- **網站在推播後顯示舊內容：**&#x200B;請確認webhook正在將事件傳送至Cloud Manager，然後檢查最新同步處理工作的狀態。
- **同步處理錯誤`Unable to fetch hlxignore: 401`：** `cm-byog`密碼不正確。 使用步驟9中的秘密重新建立檔案。
- **連結至其他網站的存放庫：** Cloud Manager存放庫一次只能連結至一個網站。 若要跨網站共用存放庫，請使用[Repoless](https://www.aem.live/docs/repoless)。

如需詳細資訊，請檢視[疑難排解中的自攜Git](https://www.aem.live/developer/byo-git#troubleshooting)。
