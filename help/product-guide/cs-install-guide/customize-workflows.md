---
title: 設定和自訂工作流程
description: 瞭解如何設定和自訂工作流程
exl-id: a5742082-cc0b-49d9-9921-d0da1b272ea5
feature: Workflow Configuration
role: Admin
level: Experienced
source-git-commit: 026d75e69ef002607ac375cf1af7d055fcc22b38
workflow-type: tm+mt
source-wordcount: '1477'
ht-degree: 2%

---

# 設定和自訂工作流程 {#id181AI0OJ0RO}

工作流程可讓您自動化Adobe Experience Manager \(AEM\)活動。 工作流程包含一系列以特定順序執行的步驟。 您可以定義要在每個步驟上執行的不同活動。 例如，您可以在建立主題稽核時，傳送電子郵件通知給群組中的所有稽核者。 或者，當輸出產生工作完成時，傳送通知給發佈者。

如需AEM工作流程的詳細資訊，請參閱：

- [管理工作流程執行個體](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html?lang=zh-Hant)

- 套用及參與工作流程： [使用專案工作流程](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/projects/workflows.html?lang=zh-Hant)。


本主題中的各節將逐步引導您瞭解在AEM Guides中提供的預設工作流程中可以進行的各種自訂。

## 自訂稽核工作流程 {#id176NE0C00HS}

每個組織的內容製作團隊都會以特定方式運作，以符合其業務需求。 某些組織設有專屬的編輯者，而其他組織則可設有自動編輯稽核系統。 例如，在組織中，典型的撰寫和發佈工作流程可能包括這樣的任務 — 每當作者完成編寫內容時，它會自動轉給稽核者，當稽核完成時，它就會轉給發佈者用於產生最終輸出。 在AEM中，您對內容和資產執行的活動可以程式形式合併，並對應至AEM工作流程。 如需AEM工作流程的詳細資訊，請參閱AEM檔案中的[管理工作流程](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html?lang=zh-Hant)。

AEM Guides可讓您自訂預設的稽核工作流程。 您可以搭配其他撰寫或發佈工作流程，使用下列四個自訂檢閱相關流程。

- **建立稽核**：此程式準備建立稽核任務所需的中繼資料。 例如，它會指派審閱許可權給審閱者、將主題的狀態設定為審閱、設定審閱時間表等等。 在四個處理程式中，這是唯一必須包含在自訂工作流程中的強制處理程式。 在工作流程中，您可以選擇包含或排除其他三個處理序。

- **指派稽核工作**：此程式會建立稽核工作，並將工作通知傳送給發起者和稽核者。

- **傳送稽核電子郵件**：此程式會將稽核電子郵件傳送給發起人和稽核者。

- **將工作排程為關閉檢閱**：此程式可確保檢閱程式在到達截止日期時完成。


建立自訂稽核工作流程時，第一項工作是設定「建立稽核」程式所需的必要中繼資料。 若要這樣做，您可以建立ECMA指令碼。 以下提供指派中繼資料的ECMA指令碼範例，供主題和地圖使用。

主題&#x200B;**的**

```javascript
var workflowdata=workItem.getWorkflowData();
workflowdata.getMetaDataMap().put("initiator","admin");
workflowdata.getMetaDataMap().put("operation","AEM_REVIEW");
workflowdata.getMetaDataMap().put("orgTopics","/content/dam/xml-solution/review.xml");
workflowdata.getMetaDataMap().put("payloadJson","{\"base\":\"/content/dam/xml-solution\",\"asset\":[\"/content/dam/xml-solution/review.xml\"],\"referrer\":\""}");
workflowdata.getMetaDataMap().put("deadline","2017-06-27T13:19:00.000+05:30");
workflowdata.getMetaDataMap().put("title","Review through custom workflow");
workflowdata.getMetaDataMap().put("description","Initiate this review process using the AEM workflow");
workflowdata.getMetaDataMap().put("assignee","user-one", "user-two");
workflowdata.getMetaDataMap().put("status","1");
workflowdata.getMetaDataMap().put("projectPath","/content/projects/review");
workflowdata.getMetaDataMap().put("startTime", System.currentTimeMillis());
workflowdata.getMetaDataMap().put("reviewType", "AEM");
workflowdata.getMetaDataMap().put("versionJson", "[{\"path\":\"GUID-ca6ae229-889a-4d98-a1c6-60b08a820bb3.dita\",\"review\":true,\"version\":\"1.0\",\"reviewers\":[\"projects-samplereviewproject-owner\"]}]");
workflowdata.getMetaDataMap().put("isDitamap","false");
```

地圖的&#x200B;**&#x200B;**

```javascript
var workflowdata = workItem.getWorkflowData();
workflowdata.getMetaDataMap().put("initiator", "admin");
workflowdata.getMetaDataMap().put("operation", "AEM_REVIEW");
workflowdata.getMetaDataMap().put("orgTopics", "GUID-ae42f13c-7201-4453-9a3a-c87675a5868e.dita|GUID-28a6517b-1b62-4d3a-b7dc-0e823225b6a5.dita|GUID-dd699e10-118d-4f1b-bf19-7f1973092227.dita|");
var payloadJson = "{\"referrer\":\"\",\"rootMap\":\"GUID-17feb385-acf3-4113-b838-77b11fd6988d.ditamap\",\"asset\":[\"GUID-17feb385-acf3-4113-b838-77b11fd6988d.ditamap\"],\"base\":\"/content/dam\"}";
workflowdata.getMetaDataMap().put("payloadJson", payloadJson);
workflowdata.getMetaDataMap().put("deadline", "2047-06-27T13:19:00.000+05:30");
workflowdata.getMetaDataMap().put("title", "Review task via workflow with map");
workflowdata.getMetaDataMap().put("description", "Review task via workflow with map Description");
workflowdata.getMetaDataMap().put("assignee", "user-one");
workflowdata.getMetaDataMap().put("status", "1");
workflowdata.getMetaDataMap().put("projectPath", "/content/projects/review_project_via_workflow");
workflowdata.getMetaDataMap().put("startTime", new Date().getTime());
var versionJson = "[{\"path\":\"GUID-ae42f13c-7201-4453-9a3a-c87675a5868e.dita\",\"version\":\"1.0\",\"review\":true,\"reviewers\":[\"starling-regression-user\"]},{\"path\":\"GUID-28a6517b-1b62-4d3a-b7dc-0e823225b6a5.dita\",\"version\":\"1.0\",\"review\":true,\"reviewers\":[\"starling-regression-user\"]},{\"path\":\"GUID-dd699e10-118d-4f1b-bf19-7f1973092227.dita\",\"version\":\"1.0\",\"review\":true,\"reviewers\":[\"starling-regression-user\"]}]";
workflowdata.getMetaDataMap().put("versionJson", versionJson);
workflowdata.getMetaDataMap().put("notifyViaEmail", "true");
workflowdata.getMetaDataMap().put("allowAllReviewers", "false");
workflowdata.getMetaDataMap().put("isDitamap", "true");
workflowdata.getMetaDataMap().put("ditamap", "GUID-17feb385-acf3-4113-b838-77b11fd6988d.ditamap");
var ditamapHierarchy = "[{\"path\":\"GUID-17feb385-acf3-4113-b838-77b11fd6988d.ditamap\",\"items\":[{\"path\":\"GUID-db5787bb-5467-4dc3-b3e5-cfde562ee745.ditamap\",\"items\":[{\"path\":\"GUID-ae42f13c-7201-4453-9a3a-c87675a5868e.dita\",\"items\":[],\"title\":\"\"},{\"path\":\"GUID-28a6517b-1b62-4d3a-b7dc-0e823225b6a5.dita\",\"items\":[],\"title\":\"\"}],\"title\":\"\"},{\"path\":\"GUID-dd699e10-118d-4f1b-bf19-7f1973092227.dita\",\"items\":[],\"title\":\"\"}]}]";
workflowdata.getMetaDataMap().put("ditamapHierarchy", ditamapHierarchy);
```

您可以在`/etc/workflows/scripts`節點中建立這些指令碼。 下表說明上述兩個ECMA指令碼所指派的屬性。

| 屬性 | 類型 | 說明 |
|--------|----|-----------|
| `initiator` | 字串 | 起始稽核任務之使用者的使用者ID。 |
| `operation` | 字串 | 設定為`AEM_REVIEW`的靜態值。 |
| `orgTopics` | 字串 | 共用以供檢閱的主題路徑。 指定多個以逗號分隔的主題。 |
| `payloadJson` | JSON 物件 | 指定下列值： -   `base`：包含已傳送供檢閱之主題的父資料夾路徑。 <br> -   `asset`：傳送供檢閱之主題的路徑。 <br> -   `referrer`：留空。 |
| `deadline` | 字串 | 以`yyyy-MM-dd'T'HH:mm:ss.SSSXXX`格式指定時間。 |
| `title` | 字串 | 輸入稽核任務的標題。 |
| `description` | 字串 | 輸入複查工作的說明。 |
| `assignee` | 字串 | 要傳送主題以供檢閱之使用者的使用者ID。 |
| `status` | 整數 | 設定為1的靜態值。 |
| `startTime` | 長 | 使用`System.currentTimeMillis()`函式取得目前系統時間。 |
| `projectPath` | 字串 | 將指派稽核任務的稽核專案路徑，例如： /content/projects/samplereviewproject。 |
| `reviewType` | 字串 | 靜態值「AEM」。 |
| `versionJson` | JSON 物件 | versionJson是正在稽核的主題清單，其中每個主題物件都有以下結構{ &quot;path&quot;： &quot;/content/dam/1-topic.dita&quot;， &quot;version&quot;： &quot;1.1&quot;， &quot;review&quot;： true， &quot;reviewers&quot;： [&quot;projects-we_retail-editor&quot;] } |
| `isDitamap` | 布林值 | false/true |
| `ditamapHierarchy` | JSON 物件 | 若已傳送地圖以供檢閱，則值應如下：[ &lbrace; &quot;path&quot;： &quot;GUID-f0df1513-fe07-473f-9960-477d4df29c87.ditamap&quot;， &quot;items&quot;： [ { &quot;path&quot;： &quot;GUID-9747e8ab-8cf1-45dd-9e20-d47d482f667d.dita&quot;， &quot;title&quot;： 「」，「items」： [] } ] ]。 |
| `ditamap` | 字串 | 指定稽核任務的ditamap路徑 |
| `allowAllReviewers` | 布林值 | false/true |
| `notifyViaEmail` | 布林值 | false/true |


建立指令碼後，請先呼叫它，然後再在工作流程中呼叫建立檢閱程式。 然後，根據您的需求，您可以呼叫其他稽核工作流程處理。

### 從永久刪除組態中移除複查工作流程

若要改善工作流程引擎效能，您可以定期從AEM存放庫中清除已完成的工作流程例項。 如果您使用預設的AEM設定，則會在特定時段後清除所有已完成的工作流程執行個體。 這也會導致所有稽核工作流程從AEM存放庫清除。

您可以從自動永久刪除組態中移除稽核工作流程模型\（資訊\），以防止稽核工作流程自動永久刪除。 您必須使用&#x200B;**Adobe Granite工作流程清除組態**，才能從自動清除清單中移除稽核工作流程模型。

在&#x200B;**Adobe Granite工作流程清除設定**&#x200B;中，請確定您至少列出一個可以安全清除的工作流程。 例如，您可以使用AEM Guides建立的下列任何工作流程：

- /etc/workflow/models/publishditamap/jcr：content/model
- /etc/workflow/models/post-dita-project-creation-tasks/ jcr：content/model

在&#x200B;**Adobe Granite工作流程清除組態**&#x200B;中新增工作流程，可確保AEM僅清除組態中列出的工作流程。 這可防止AEM清除稽核工作流程資訊。

如需有關設定&#x200B;**Adobe Granite工作流程清除設定**&#x200B;的詳細資訊，請參閱AEM檔案中的&#x200B;*管理工作流程執行個體*。

### 自訂電子郵件範本

許多AEM Guides工作流程會使用電子郵件通知。 例如，如果您啟動稽核任務，則會傳送電子郵件通知給稽核者。 不過，若要確保電子郵件通知已傳送，您必須在AEM中啟用此功能。 若要在AEM中啟用電子郵件通知，請參閱AEM檔案中的文章[傳送電子郵件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=zh-Hant#sending-email)。

AEM Guides包含一組您可自訂的電子郵件範本。 執行以下步驟來自訂這些範本：

1. 使用封裝管理員下載`/libs/fmdita/mail`檔案。

   >[!NOTE]
   >
   > 請勿在``libs``節點中使用預設組態檔中的任何自訂專案。 您必須在``apps``節點中建立``libs``節點的覆蓋，並僅更新``apps``節點中的必要檔案。

1. 郵件資料夾包含下列可自訂的範本：

   | 範本檔案名稱 | 說明 |
   |-----------------|-----------|
   | closereview.html | 此電子郵件範本在稽核任務關閉時使用。 |
   | createreview.html | 建立新稽核任務時會使用此電子郵件範本。 |
   | reviewapproval.css | 此CSS檔案包含電子郵件範本的樣式。 |


## 自訂輸出後產生工作流程 {#id17A6GI004Y4}

AEM Guides可讓您靈活指定輸出後產生工作流程。 您可以在使用AEM Guides產生的輸出上執行一些後續處理工作。 例如，您可能會想要在產生的AEM Site輸出上套用一些CQ標籤，或在PDF輸出上設定某些屬性，或者您可能會想要在產生輸出後傳送電子郵件給一組使用者。

您可以建立新的工作流程模型，以用作輸出後產生工作流程。 觸發後置輸出產生工作流程時，輸出產生工作流程會透過工作流程中繼資料對應分享內容相關資訊，您可以使用這些資訊對產生的輸出執行處理。 下表說明作為中繼資料共用的內容資訊：

| 屬性 | 類型 | 說明 |
|--------|----|-----------|
| ``outputName`` | 字串 | 用來產生輸出的輸出預設集名稱。 |
| `generatedPath` | 字串 | DAM中儲存所產生輸出的路徑。 |
| `outputType` | com.adobe.fmdita.output.OutputType | 輸出預設集的型別。 |
| `outputTitle` | 字串 | 輸出預設集的標題。 |
| `outputHistoryPath` | 字串 | 歷史記錄節點的存放庫路徑。 |
| `isSuccess` | 布林值 | 描述輸出產生程式最終狀態（成功或失敗）的旗標。 |
| `logPath` | 字串 | DAM中儲存輸出產生記錄的路徑。 |
| `generatedTime` | 長 | 觸發輸出產生程式的時間。 |
| `initiator` | 字串 | 觸發輸出產生工作流程的使用者的使用者ID。 |

若要使用輸出產生中繼資料，您可以建立ECMA指令碼或OSGi套件。 以下提供使用中繼資料的ECMA指令碼範例：

>[!NOTE]
>
> 您可以在``/etc/workflows/scripts``節點中建立此指令碼。

```javascript
var session = workflowSession.getSession(); // Obtain session object to read/write the repository.
var payload = workItem.getWorkflowData().getPayload().toString(); // Get the workflow payload (the ditamap file on which the generation was triggered)
var metadata = workItem.getWorkflowData().getMetaDataMap(); // Get the workflow metadata object
var generatedPath = metadata.get("generatedPath"); // supplied by AEM Guides
var username = metadata.get("initiator"); // supplied by AEM Guides
var successful = metadata.get("isSuccess"); // supplied by AEM Guides
var title = metadata.get("outputTitle"); // supplied by AEM Guides
var subject = "Output Generation Finished";
var message = "Generation of output " + title + " just finished " + 
(successful ? "successfully. " : "unsuccessfully. ");
    message += "It was triggered by " + username;    
if (successful) {
    message += "<br/><br/>The path to the generated output is " + 
generatedPath;
}
/*
    MailerAPI.sendMail("dl-docs-authors", subject, message);
*/
```

建立指令碼後，請呼叫工作流程中的自訂指令碼。 然後，根據您的需求，您可以呼叫其他工作流程處理。 設計好自訂工作流程後，請呼叫&#x200B;*完成產生貼文*，作為工作流程程式的最後一步。 *完成產生後工作*&#x200B;步驟可確保輸出產生工作的狀態在輸出產生程式完成時更新為&#x200B;*已完成*。 建立自訂輸出後產生工作流程後，您可以使用任何輸出產生預設集進行設定。 在必要預設集的&#x200B;*執行產生後工作流程*&#x200B;屬性中選取必要的工作流程。 當您使用設定的輸出預設集執行輸出產生工作時，工作狀態\（在[輸出]索引標籤中\）會變更為&#x200B;*後續處理*。
