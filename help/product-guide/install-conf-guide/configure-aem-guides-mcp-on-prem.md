---
title: 設定AEM Guides On-Premise的MCP連線設定
description: 瞭解如何為AEM Guides On-Premise設定MCP連線設定。
meta-feature: Authoring
meta-product: Experience Manager, Experience Manager Guides
meta-role: Admin
meta-type: Documentation
source-git-commit: e234425f1e277990de25057971f3e2453c93360f
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 3%
---

# 設定Experience Manager Guides （內部部署）的MCP連線設定

Claude、Cursor和Codex等AI工具可使用模型上下文通訊協定(MCP)連線至Experience Manager Guides。 您可以從「Adobe Experience Manager Web主控台組態」頁面設定MCP連線和驗證設定。

可用的設定可控制Token處理、不含反向連結資訊的請求，以及AEM作者執行個體的外部URL。

## 設定登入權杖處理

若要設定登入權杖處理方式，請執行以下步驟：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```
   http://<server name>:<port>/system/console/configMgr
   ```

2. 搜尋並選取&#x200B;**AEM Guides OAuth PKCE權杖包裝函式**。

3. 設定下列屬性：

   | 屬性 | 預設 | 說明 |
   |---|---|---|
   | Granite基底URL | `http://localhost:4502` | 指定AEM在驗證期間用來與製作執行個體通訊的URL。 只有在您的編寫執行個體使用不同的連線埠時，才能變更預設連線埠4502。 |
   | Granite逾時（毫秒） | `5000` | 指定等待驗證要求完成的最長時間（毫秒）。 |

4. 選取「**儲存**」。

## 設定不含反向連結資訊的請求

>[!NOTE]
>
> 只有在使用「游標」時，才需要設定此設定。

有些MCP使用者端（包括Cursor）可能會傳送不含反向連結資訊的請求。 若要允許這些請求，請依照以下方式設定Apache Sling反向連結篩選器：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```
   http://<server name>:<port>/system/console/configMgr
   ```

2. 搜尋並選取&#x200B;**Apache Sling反向連結篩選器**。

3. 在&#x200B;**允許空白**&#x200B;屬性中，將值設定為`true`。

   此設定允許在驗證期間不包含反向連結資訊的請求。

4. 選取「**儲存**」。

## 為作者執行個體設定外部URL

**Day CQ Link Externalizer**&#x200B;服務可讓您集中定義用於為資源路徑加上前置詞的外部URL，包括AEM作者執行個體的URL。

若要設定外部URL，請執行下列步驟：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```
   http://<server name>:<port>/system/console/configMgr
   ```

2. 搜尋並選取&#x200B;**Day CQ Link Externalizer**。

3. 在&#x200B;**網域**&#x200B;底下，使用下列格式新增或更新`author`對應：

   ```
   author [scheme://]server[:port][/contextpath]
   ```

   例如：

   ```
   author https://author.mycompany.com
   ```

4. 選取「**儲存**」。