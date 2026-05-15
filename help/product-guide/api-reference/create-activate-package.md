---
title: 用於建立和啟用套件的REST API
description: 瞭解用於建立和啟用套件的REST API
exl-id: 90686f77-a769-44bc-90eb-116cf9d0341e
feature: Rest API Packages
role: Developer
level: Experienced
TQID: https://experienceleague.adobe.com/cJUVS3QdzVhnZjFF7uoHfpOSBefgm5W2jh-kWM1PvmE
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: a3bd6397-2eb2-4908-a61c-226e26855dcaid: c6d09140-3c91-45d3-b7ed-b681af752f43
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 181
ht-degree: 0%

---

# 用於建立和啟用套件的REST API {#id198CF0260Y4}

下列REST API可讓您建立和啟用CRX套件。

## 建立及啟用封裝

建立及啟用CRX封裝的POST方法。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/fmdita/activate

**引數**：
請求查詢包含JSON規則字串。 POST要求的內容型別必須設定為`application/json; charset=UTF-8`。

**範例**：
以下範例顯示使用curl命令的API呼叫：

```XML
curl -u <*username*>:<*password*> -H "Content-Type: application/json; charset=UTF-8"  -k -X POST -d "{[JSON rules string](create-activate-package-java.md#example-create-activate-package-id198JH0B905Z)}" http://<*aem-guides-server*>:<*port-number*>/bin/fmdita/activate
```


**選用引數**

`activationTarget`

**有效值**

Cloud Service的`preview`或`publish`，以及內部部署軟體的`publish`

- 對於Cloud Service，如果引數包含無效值，則封裝啟用會失敗。

- 對於內部部署軟體，如果引數包含無效的值，則會記錄錯誤，並使用預設值`publish`完成發佈。

如果您未定義選用引數`activationTarget`，它會使用Cloud Service和On-premise Software的預設發佈代理程式來啟動。



以下範例顯示使用具有選用引數的curl命令的API呼叫：


```XML
curl -u <*username*>:<*password*> -H "Content-Type: application/json; charset=UTF-8"  -k -X POST -d "{[JSON rules string](create-activate-package-java.md#example-create-activate-package-id198JH0B905Z)}" http://<*aem-guides-server*>:<*port-number*>/bin/fmdita/activate?activationTarget=`<validActivationTargetValue>`
```
