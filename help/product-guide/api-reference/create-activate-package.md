---
title: 用於創建和啟動包的 REST API
description: 瞭解用於創建和啟動程式包的 REST API
exl-id: 90686f77-a769-44bc-90eb-116cf9d0341e
feature: Rest API Packages
role: Developer
level: Experienced
source-git-commit: 32da48d82b1267bb220424edf385035426293b66
workflow-type: tm+mt
source-wordcount: '160'
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

`preview` 或 `publish` 用于Cloud Service和 `publish` 內部部署軟體

如果參數包含無效值，則包的啟用將失敗。 以下範例顯示了使用 curl 命令和可選參數的 API 呼叫：


    &#39;&#39;&#39;XML
    
    curl -u &lt;*username*>：&lt;*password*> -H “Content-Type： 應用程式/json;charset=UTF-8“ -k -X POST -d ”{[JSON rules string]（create-activate-package-java.md#example-create-activate-package-id198JH0B905Z）}“ http://&lt;*aem-guides-server*>：&lt;*port-number*>/bin/fmdita/activate？activationTarget=&#39;&lt;validActivationTargetValue>&#39;&#39;
    &#39;&#39;
&lt;/validActivationTargetValue>&lt;/*port-number*>&lt;/*aem-guides-server*>&lt;/*password*>&lt;/*username*>