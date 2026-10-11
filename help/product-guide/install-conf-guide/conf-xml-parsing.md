---
title: 為雲端服務和內部部署設定XML剖析實體
description: 瞭解如何為雲端服務和內部部署設定XML剖析實體
feature: Output Generation
role: Admin
level: Experienced
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
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%
---
# 設定XML剖析器實體大小限制

Experience Manager Guides可讓您設定XML剖析器在發佈期間接受的總實體大小限制。 這有助於防止XML實體擴充攻擊和處理過大負載等問題。

>[!NOTE]
>
>您可以設定XML剖析器在發佈期間接受的總實體大小限制，降低XML實體擴充攻擊和超大負載處理等風險。 Java 21和Java 25的實體大小限制處理方式不同；因此，建議升級至Java 25的環境檢閱和驗證其設定，以確保發佈工作流程繼續運作且沒有錯誤。

此設定涉及兩個相關屬性：

* **套用XML剖析器實體大小總計限制** (`dxml.publish.xml.apply.total.entity.size.limit`)：啟用或停用實體大小總計限制檢查。
* **XML剖析器實體大小總計限制** (`dxml.publish.xml.total.entity.size.limit`)：指定啟用套用旗標時，套用至安全XML剖析器的JAXP `totalEntitySizeLimit`值（字元）。

下列標籤提供根據Experience Manager Guides設定來設定這些屬性的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[組態覆寫](download-install-config-override.md)中提供的指示來建立組態檔。

1. 在設定檔案中，提供下列（屬性）詳細資訊：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService` | `dxml.publish.xml.apply.total.entity.size.limit` | **預設值：** &quot;true&quot; |
   | `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService` | `dxml.publish.xml.total.entity.size.limit` | **預設值：** &quot;50000000&quot; |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;*com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService*&#x200B;套件。

1. 根據您的要求進行下列設定：

   * **套用XML剖析器實體大小總計限制** (`dxml.publish.xml.apply.total.entity.size.limit`)：預設會停用此設定。
   * **XML剖析器實體大小總計限制** (`dxml.publish.xml.total.entity.size.limit`)：根據預設，此值設定為`50000000`個字元。 此設定只有在啟用&#x200B;**套用XML剖析器實體大小總計限制**&#x200B;設定時才生效。

1. 選取「**儲存**」。

>[!ENDTABS]



