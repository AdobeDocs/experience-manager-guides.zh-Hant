---
title: 設定中繼資料屬性的忽略清單
description: 瞭解如何在AEM Guides中設定中繼資料屬性的忽略清單。
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# 設定中繼資料屬性的忽略清單

編輯檔案時，對&#x200B;**檔案屬性**&#x200B;下可用的中繼資料欄位所做的任何變更，或套用在後端時，都會在檔案版本上觸發星號(*)。 為了防止系統產生的中繼資料更新影響此指標，管理員可以設定中繼資料屬性的忽略清單。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在組態檔中，提供下列（屬性）詳細資訊，以設定已變更版本&#x200B;**的**&#x200B;忽略中繼資料屬性。


| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.dirtychecker.ignoremetadata` | `<comma-separated list / array of metadata properties>` |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 在&#x200B;*XmlEditorConfig*&#x200B;設定中，瀏覽至&#x200B;**忽略已更新版本的中繼資料屬性**&#x200B;選項。

   檢閱目前設定為忽略的預設中繼資料屬性清單。

1. 根據需求新增或移除中繼資料屬性。
1. 選取&#x200B;**儲存**&#x200B;以儲存更新的組態。


>[!ENDTABS]

## 忽略清單中的預設中繼資料屬性

AEM Guides在忽略清單中包含一組預設的中繼資料屬性。 您可以視需要修改此清單，以新增或移除中繼資料屬性。

* &quot;jcr:mixinTypes&quot;，
* &quot;jcr:primaryType&quot;，
* &quot;jcr:frozenMixinTypes&quot;，
* &quot;jcr:frozenPrimaryType&quot;，
* &quot;jcr:frozenUuid&quot;，
* &quot;jcr:uuid&quot;，
* &quot;dam:extracted&quot;，
* &quot;jcr:lastModified&quot;，
* &quot;jcr:lastModifiedBy&quot;，
* &quot;dc:modified&quot;，
* &quot;dam:sha1&quot;，
* &quot;dam:size&quot;，
* &quot;guides:wordCount&quot;，
* &quot;dam:scene7UploadTimeStamp&quot;，
* &quot;dam:scene7LastModified&quot;

只有未包含在忽略清單中的中繼資料屬性才會被視為標籤檔案版本已變更。

**父級主題：**[&#x200B;自訂編輯器](customize-overview.md)
