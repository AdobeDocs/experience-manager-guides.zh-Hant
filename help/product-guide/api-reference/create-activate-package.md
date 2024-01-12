---
title: 用於建立和啟用套件的REST API
description: 瞭解用於建立和啟用套件的REST API
exl-id: 90686f77-a769-44bc-90eb-116cf9d0341e
feature: Rest API Packages
role: Developer
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# 用於建立和啟用套件的REST API {#id198CF0260Y4}

以下REST API可讓您建立和啟用CRX套件。

## 建立及啟用封裝

建立及啟用CRX封裝的POST方法。

**請求URL**： http://*&lt;aem-guides-server>*： *&lt;port-number>*/bin/fmdita/activate

**引數**：要求查詢包含JSON規則字串。 POST要求的內容型別必須設定為 `application/json; charset=UTF-8`.

**範例**：下列範例顯示使用curl命令的API呼叫：

    ```
    curl -u &lt;*username*>：&lt;*password*> -H &quot;Content-Type： application/json； charset=UTF-8&quot; -k -XPOST-d &quot;{[JSON規則字串](create-activate-package-java.md#example-create-activate-package-id198JH0B905Z)}&quot; http://&lt;*aem-guides-server*>：&lt;*port-number*>/bin/fmdita/activate
    ```
