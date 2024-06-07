---
title: 用於創建和啟動包的 REST API
description: 瞭解用於創建和啟動程式包的 REST API
exl-id: 90686f77-a769-44bc-90eb-116cf9d0341e
feature: Rest API Packages
role: Developer
level: Experienced
source-git-commit: b95a64ca2e8ebffebec3d8ff8704f76f7faceca2
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# 用於創建和啟動包的 REST API {#id198CF0260Y4}

以下 REST API 允許您建立和啟動 CRX 套件。

## 建立並啟動套裝

建立並啟用CRX套裝的POST方法。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;port-number\>*/bin/fmdita/activate&lt;/port-number\>&lt;/aem-guides-server\>

**參數：**
該請求 查詢包含 JSON 規則字串。 POST 要求的內容類型必須設置為 `application/json; charset=UTF-8`。

**範例**：
以下範例顯示了使用 curl 命令的 API 呼叫：

```XML
curl -u <*username*>:<*password*> -H "Content-Type: application/json; charset=UTF-8"  -k -X POST -d "{[JSON rules string](create-activate-package-java.md#example-create-activate-package-id198JH0B905Z)}" http://<*aem-guides-server*>:<*port-number*>/bin/fmdita/activate
```


**可選參數**

`activationTarget`

**有效值**

`preview` 或 `publish` 用於Cloud Service和 `publish` 內部部署軟體

- 對於Cloud Service，如果參數包含無效值，則包啟用失敗。

- 對於內部部署軟體，如果參數包含無效值，則會記錄錯誤，並使用預設值 . `publish`

如果未定義可選參數 ， `activationTarget`則會使用 Cloud Service 和本地軟體的預設 發佈 代理啟動。



以下範例顯示了使用 curl 命令和可選參數的 API 呼叫：


    &#39;&#39;&#39;XML
    
    curl -u &lt;*username*>：&lt;*password*> -H “Content-Type： 應用程式/json;charset=UTF-8“ -k -X POST -d ”{[JSON rules string]（create-activate-package-java.md#example-create-activate-package-id198JH0B905Z）}“ http://&lt;*aem-guides-server*>：&lt;*port-number*>/bin/fmdita/activate？activationTarget=&#39;&lt;validActivationTargetValue>&#39;&#39;
    &#39;&#39;
&lt;/validActivationTargetValue>&lt;/*port-number*>&lt;/*aem-guides-server*>&lt;/*password*>&lt;/*username*>