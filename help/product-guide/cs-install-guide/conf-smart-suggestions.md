---
title: 設定智慧型建議以進行編寫
description: 瞭解如何設定智慧型撰寫建議
source-git-commit: 1cdad275651b78d794ebc3f4ad9ead266ebeb0bd
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 1%

---

# 設定AI支援的智慧型建議以進行編寫

身為管理員，您可以為作者設定「智慧型建議」功能。 智慧型建議服務受到Adobe IMS驗證型驗證的保護。 將您的環境與Adobe的安全權杖型驗證工作流程整合，並開始使用新的智慧建議功能。 以下設定可協助您新增 **AI設定** 索引標籤移至資料夾設定檔。 新增後，您便可以在網頁編輯器中使用智慧型建議功能。

## 在Adobe Developer Console中建立IMS設定

執行以下步驟，在Adobe Developer主控台中建立IMS設定：
1. Launch [Adobe Developer Console](https://developer.adobe.com/console).
1. 成功登入開發人員控制檯後，您將檢視 **首頁** 畫面。 此 **首頁** 畫面可讓您輕鬆找到資訊和快速連結，包括專案和下載的頂端導覽連結。
1. 若要建立新的空白專案，請選取  **建立新專案** 從  **快速入門** 連結。
   ![快速入門連結](assets/conf-ss-quick-start.png) {width="550" align="left"}
   *建立新專案。*

1. 選取  **新增API**  從  **專案** 畫面。  此 **新增API** 畫面隨即顯示。 此畫面會顯示所有可用的API、事件和服務，供您用來開發應用程式的Adobe產品和技術。

1. 選取 **I/O管理API** 以將其新增至您的專案。
   ![IO管理API](assets/confi-ss-io-management.png)
   *新增I/O Management API至您的專案。*

1. 建立新的 **OAuth認證** 並儲存。
   ![設定API中的OAuth認證磚](assets/conf-ss-OAuth-credential.png) {width="3000" align="left"}
   *設定API的OAuth認證。*

1. 在  **專案** 索引標籤，選擇 **OAuth伺服器至伺服器** 選項，然後選取新建立的認證。

1. 選取 **OAuth伺服器對伺服器** 檢視專案認證詳細資料的連結。

   ![連線的認證](assets/conf-ss-connected-credentials.png) {width="800" align="left"}

   *連線至專案以檢視認證詳細資料。*
1. 複製CLIENT_ID和CLIENT_SECRET金鑰。

您現在已設定OAuth驗證詳細資料。 請隨時使用這兩個金鑰，因為下一個區段需要用到它們。

### 將IMS設定新增至環境

執行以下步驟，將IMS設定新增至環境：

1. 開啟Experience Manager，然後選取包含您要設定環境的程式。
1. 切換至 **環境** 標籤。
1. 選取您要設定的環境名稱。 這應該會將您導覽至環境資訊頁面。
1. 切換至 **設定** 標籤。
1. 新增CLIENT_ID和CLIENT_SECRET金鑰，如下列熒幕擷圖所示。 請確定您使用的名稱和設定與以下醒目提示的名稱和設定相同。
   ![環境設定](assets/conf-ss-environment.png) {width="800" align="left"}
   *新增環境設定詳細資料。*




新增IMS設定至環境後，請使用OSGi執行以下步驟將這些屬性與AEM Guides連結：

1. 在您的Cloud Manager Git專案程式碼中，新增以下兩個指定的檔案(針對檔案內容，檢視 [附錄](#appendix))。

   * `com.adobe.fmdita.ims.service.ImsOauthUserAccountHeadersImpl.cfg.json`
   * `com.adobe.fmdita.smartsuggest.service.SmartSuggestConfigurationConsumer.cfg.json`
1. 確保新新增的檔案包含在您的 `filter.xml`.
1. 認可並推送您的Git變更。
1. 執行管道以在環境中套用變更。

完成此操作後，您應該能夠使用智慧型建議功能。



## 附錄 {#appendix}

**檔案**：
`com.adobe.fmdita.ims.service.ImsOauthUserAccountHeadersImpl.cfg.json`

**內容**：

```
{
  "client.id": "$[secret:CLIENT_ID]",
  "client.secret": "$[secret:CLIENT_SECRET]",
  "ims.url": "https://ims-na1.adobelogin.com"
}
```

**檔案**： `com.adobe.fmdita.smartsuggest.service.SmartSuggestConfigurationConsumer.cfg.json`

**內容**：

```
{
  "smart.suggestion.flag":true,
  "conref.inline.threshold":0.6,
  "conref.block.threshold":0.7,
  "emerald.url":"https://adobeioruntime.net/apis/543112-smartsuggest/emerald/v1",
  "instance.type":"prod"
}
```

## 智慧建議組態詳細資料

| 關鍵 | 說明 | 允許的值 | 預設值 |
|---|---|---|---|
| smart.suggestion.flag | 控制是否啟用智慧建議 | true/false | false |
| conref.inline.threshold | 此臨界值可控制針對使用者目前輸入的標籤所擷取建議的精確度/召回率。 | 從–1.0到1.0的任何值。 | 0.6 |
| conref.block.threshold | 此臨界值會控制在整個檔案中為標籤擷取的建議精確度/召回率。 | 從–1.0到1.0的任何值。 | 0.7 |
| emerald.url | 翡翠向量資料庫的端點 | [https://adobeioruntime.net/apis/543112-smartsuggest/emerald/v1](https://adobeioruntime.net/apis/543112-smartsuggest/emerald/v1) | [https://adobeioruntime.net/apis/543112-smartsuggest/emerald/v1](https://adobeioruntime.net/apis/543112-smartsuggest/emerald/v1) |
| instance.type | AEM執行個體的型別。 請確定此名稱對於已設定智慧建議的每個AEM執行個體都是唯一的。 使用案例是在Stage環境中以「instance.type」=「stage」測試功能，同時在「prod」上也設定此功能。 | 任何可識別環境的唯一關鍵值。 僅限 *英數字元* 允許使用值。 &quot;dev&quot;/&quot;stage&quot;/&quot;prod&quot;/&quot;test1&quot;/&quot;stage2&quot; | &quot;prod&quot; |

完成設定後，智慧型建議圖示會顯示在Web編輯器的右側面板中。 編輯主題時，您可以檢視智慧型建議清單。 如需詳細資訊，請檢視 [以AI為基礎的智慧型製作建議](../user-guide/authoring-ai-based-smart-suggestions.md) 區段的URL來識別Experience Manager。
