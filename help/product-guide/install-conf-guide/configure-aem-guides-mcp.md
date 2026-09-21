---
title: 為Adobe Experience Manager Guides設定MCP
description: 瞭解如何將AI助理連線到Experience Manager Guides MCP伺服器，以進行Cloud Service和內部部署
meta-feature: Authoring
meta-product: Experience Manager, Experience Manager Guides
meta-role: User
meta-type: Documentation
source-git-commit: e234425f1e277990de25057971f3e2453c93360f
workflow-type: tm+mt
source-wordcount: '1539'
ht-degree: 1%
---

# 設定Experience Manager Guides MCP伺服器

本文介紹有關連線到Experience Manager Guides MCP伺服器的環境特定詳細資訊。 安裝程式會因Experience Manager Guides執行個體是執行as a Cloud Service還是內部部署而有所不同。 選取符合您環境的索引標籤。

>[!BEGINTABS]

>[!TAB Cloud Service]

## MCP伺服器端點

Experience Manager Guides透過單一HTTP端點公開其MCP功能。

| MCP伺服器 | 端點 | 說明 |
|---|---|---|
| **Experience Manager Guides** | `https://mcp.adobeaemcloud.com/adobe/mcp/guides` | 在Experience Manager Guides中使用主題與地圖、[新基準線](../user-guide/web-editor-baseline-v2.md)與報告。 |

若要探索您環境的目前工具清單，請詢問您的助理：

```
List all Experience Manager Guides tools available from the author https://author-pXXXX-eXXXX.adobeaemcloud.com and describe what they do.
```

## 為您的組織要求存取權

存取Experience Manager Guides MCP伺服器的許可權是每個組織&#x200B;**選擇加入**。 在您組織中的任何人能夠連線之前：

- 必須在您的AEM as a Cloud Service環境中啟用Experience Manager Guides 。
- 貴組織的IMS組織ID （組織ID）必須由Adobe Guides團隊加入允許清單。

若要請求存取權，請聯絡您的Adobe客戶成功團隊。

## 設定

您不會在本機安裝任何專案。 您將使用者端指向伺服器URL，並透過Adobe IMS登入流程進行驗證。

### 合唱團克勞德

按照官方逐步說明： [為AEM MCP設定Claude](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/ai-in-aem/mcp-support/chat-applications/setup-claude)。 新增自訂聯結器時，請使用Experience Manager Guides端點：

```
https://mcp.adobeaemcloud.com/adobe/mcp/guides
```

### Cursor / Visual Studio Code

將伺服器新增至您的MCP設定。 針對游標，將其新增至`.cursor/mcp.json`：

```json
{
  "mcpServers": {
    "aem-guides": {
      "url": "https://mcp.adobeaemcloud.com/adobe/mcp/guides"
    }
  }
}
```

對於只支援本機(stdio)伺服器的使用者端，使用[`mcp-remote`](https://www.npmjs.com/package/mcp-remote)橋接至遠端端點：

```json
{
  "mcpServers": {
    "aem-guides": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.adobeaemcloud.com/adobe/mcp/guides"]
    }
  }
}
```

>[!TAB 內部部署]

您可以使用模型內容通訊協定(MCP)，將支援的AI使用者端連線至Experience Manager Guides內部部署執行個體。 建立連線後，使用者端即可存取您的AEM使用者帳戶可用的Experience Manager Guides操作。

所有作業都是使用&#x200B;**您的AEM身分和許可權**&#x200B;執行。 連線的使用者端只能檢視或修改您的AEM帳戶有權存取的內容和資源。

驗證使用OAuth 2.0授權代碼流程及Proof Key for Code Exchange (PKCE)。 第一次連線使用者端時，您會使用AEM進行驗證。 成功驗證後，連線會自動重新整理存取權杖。

您可以連線下列使用者端：

| 用戶端 | 連線方法 | AEM執行個體需求 |
| ------------------ | ----------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **克勞德案頭** | 案頭擴充功能(`.mcpb`) | 支援HTTP和HTTPS端點，包括可從您的公司網路存取的內部主機。 |
| **ChatGPT （網頁和案頭）** | 自訂聯結器 | 需要可公開存取的HTTPS端點以及有效的、公開信任的TLS憑證。 |
| **游標** | `~/.cursor/mcp.json`中的MCP設定 | 支援HTTP和HTTPS端點，包括可從您的公司網路存取的內部主機。 |

## 先決條件

在連線使用者端之前，請與您的AEM管理員合作以驗證下列設定：

1. **確認MCP功能已部署。**：確認MCP功能已部署並在您的Experience Manager Guides執行個體上執行。

2. **設定Granite基底URL。**：在AEM Web Console Configuration Manager (`/system/console/configMgr`)中，找到&#x200B;**Experience Manager Guides OAuth PKCE權杖包裝函式**&#x200B;設定，並確認Granite基底URL已設定。 如果Granite基底URL未正確設定，使用者端將無法建立連線。

3. **設定Day CQ Link Externalizer。**：在AEM Web Console Configuration Manager中，找到&#x200B;**Day CQ Link Externalizer**&#x200B;設定，並確認外部作者URL指向正確的AEM作者執行個體。 OAuth探索期間會使用外部作者URL。 不正確的URL會導致使用者端無法完成連線。

   如需詳細資訊，請檢視[設定AEM Guides On-Premise的MCP連線設定](./configure-aem-guides-mcp-on-prem.md)

4. **取得MCP伺服器URL。**： MCP伺服器URL使用下列格式：

   ```
   http(s)://<AEM-HOST>/bin/guides/v1/mcp/sse
   ```

   >[!NOTE]
   >
   > 設定使用者端時使用完整的SSE端點。 請勿在URL後面加上斜線。

   例如：

   **內部AEM作者執行個體：**

   ```
   http://10.42.42.20:4502/bin/guides/v1/mcp/sse
   ```

   **公用AEM作者執行個體：**

   ```
   https://author.example.com/bin/guides/v1/mcp/sse
   ```



5. **驗證您的AEM認證和許可權。**：您必須擁有適用於AEM執行個體的有效帳戶。 使用您用來登入AEM使用者介面的相同認證。 可透過MCP執行的作業是由指派給此帳戶的許可權所決定。

## 連線Claude Desktop

Claude Desktop支援案頭擴充功能(`.mcpb`)。 Experience Manager Guides MCP擴充功能會封裝連線設定，因此您不需要手動編輯MCP JSON設定。

1. 解壓縮[AEM Guides .mcpb zip檔案](./mcpbfile.zip)並取得`aem-guides-mcp.mcpb`副檔名檔案。

2. 開啟&#x200B;**Claude Desktop**&#x200B;並瀏覽至&#x200B;**設定>擴充功能**。

3. 按兩下檔案或將檔案拖曳到[擴充功能]視窗中，以安裝`aem-guides-mcp.mcpb`。

   **Adobe Experience Manager Guides MCP**&#x200B;會顯示在[安裝]對話方塊中。

4. 選取&#x200B;**安裝**。

5. 在&#x200B;**Experience Manager Guides MCP伺服器URL**&#x200B;欄位中，輸入AEM執行個體的完整SSE端點。

   例如：

   ```
   http://<AEM-HOST>:4502/bin/guides/v1/mcp/sse
   ```

6. 選取&#x200B;**儲存**，並確認擴充功能已啟用。

## 連線ChatGPT

您可以在ChatGPT中將Experience Manager Guides MCP伺服器設定為自訂聯結器。

>[!IMPORTANT]
>
> ChatGPT要求MCP伺服器必須透過&#x200B;**可公開存取的HTTPS端點使用，並具有有效、公開信任的TLS憑證**。
>
> 不支援HTTP端點、`localhost`、私人IP位址和自簽憑證。 AEM執行個體必須透過HTTPS主機公開，例如負載平衡器、反向Proxy或設定了TLS的Dispatcher。
>
> 在&#x200B;**Day CQ Link Externalizer**&#x200B;中設定的外部作者URL也必須指向公用HTTPS位址。 否則，OAuth探索中繼資料可能會通告不正確的驗證端點，並阻止登入。

1. 請確認您的MCP伺服器可在下列格式的公用HTTPS URL上使用：

   ```
   https://<PUBLIC-AEM-HOST>/bin/guides/v1/mcp/sse
   ```

   在瀏覽器中開啟端點，並確認您可以在沒有憑證警告或連線錯誤的情況下到達主機。

2. 在ChatGPT中，開啟&#x200B;**設定>外掛程式**。

   >[!NOTE]
   >
   > 聯結器的可用性取決於您的ChatGPT計畫和工作區設定。 您的工作區管理員可能需要啟用自訂或開發人員聯結器。

3. 選取要新增或建立外掛程式的選項。

4. 指定聯結器詳細資料：

   * **名稱：**&#x200B;請輸入`Experience Manager Guides`或其他描述性名稱。
   * **MCP伺服器URL：**&#x200B;請輸入公用HTTPS SSE端點。
   * **驗證：**&#x200B;選取&#x200B;**OAuth**。

   您不需要提供OAuth使用者端ID或使用者端密碼。 MCP伺服器支援自動使用者端註冊。

5. 建立聯結器。

## 連線游標

將伺服器詳細資料新增至MCP設定，在「游標」中設定Experience Manager Guides MCP伺服器。

1. 在游標中，瀏覽至&#x200B;**自訂> MCP > New**。

   游標會開啟`~/.cursor/mcp.json`組態檔。

2. 新增Experience Manager Guides MCP伺服器設定。

   例如：

   ```json
   {
     "mcpServers": {
       "aem-guides": {
         "url": "http://10.42.34.176:4502/bin/guides/v1/mcp/sse",
         "type": "http"
       }
     }
   }
   ```

3. 將範例URL取代為AEM執行個體的MCP SSE端點。

4. 儲存設定。

5. 啟用設定的MCP伺服器。

>[!ENDTABS]

## 驗證及使用Experience Manager Guides

在使用者端設定MCP連線後，請使用您的AEM帳戶進行驗證。

1. 從您的使用者端啟動驗證程式。

   * **Claude Desktop：**&#x200B;驗證流程會在Claude第一次嘗試使用Experience Manager Guides連線時開始。
   * **ChatGPT：**&#x200B;驗證會在您建立並連線Experience Manager Guides聯結器後開始。
   * **游標：**&#x200B;啟用設定的MCP伺服器並選取&#x200B;**驗證**。

2. 當AEM登入頁面在瀏覽器中開啟時，請使用您的AEM憑證登入。

3. 出現提示時核准存取權要求。

4. 驗證完成後，請返回您的使用者端。

您現在可以使用帳戶可用的Experience Manager Guides作業。 例如，嘗試以下提示：

```
List the available Experience Manager Guides operations.
```

```
Get the topic list for my map in Experience Manager Guides.
```

```
Show me the broken-link report for my map.
```

>[!NOTE]
>
> 可透過MCP使用的操作和內容由用於驗證的AEM帳戶的許可權決定。 MCP連線未提供額外的AEM許可權。

成功驗證後，使用者端會自動重新整理驗證Token。 除非工作階段過期或存取許可權遭撤銷，否則您通常不需要再次登入。

## 疑難排解連線問題

使用下列資訊來疑難排解常見的連線和驗證問題。

| 用戶端 | 問題 | 可能的原因和解決方法 |
| -------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 克勞德案頭 | 無法安裝或停用擴充功能。 | 您的Claude Desktop版本可能不支援此擴充功能。 請更新Claude Desktop，然後再試一次。 |
| 克勞德案頭 | 瀏覽器未開啟以進行驗證，或連線未完成。 | 驗證MCP伺服器URL。 它必須以`/bin/guides/v1/mcp/sse`結尾，且不應包含結尾斜線。 此外，請確認您可從電腦存取AEM執行個體。 |
| ChatGPT | ChatGPT無法連線MCP伺服器或不允許您新增聯結器。 | 確認端點可透過HTTPS公開存取。 不支援HTTP端點、`localhost`、私用IP位址和私用網路端點。 |
| ChatGPT | 顯示憑證或安全性錯誤。 | 確認伺服器使用由公開受信任憑證授權單位發行的有效未過期憑證。 不支援自我簽署憑證。 |
| ChatGPT | 驗證會重新導向不正確的主機，或在探索期間失敗。 | 確認&#x200B;**Day CQ Link Externalizer**&#x200B;中的外部作者URL指向公用HTTPS AEM作者位址。 |
| 所有使用者端 | 驗證期間註冊失敗。 | 請向您的AEM管理員確認伺服器端OAuth註冊設定。 |
| 所有使用者端 | 驗證失敗或未完成。 | 驗證Granite基底URL、Day CQ Link Externalizer設定、MCP伺服器URL以及與AEM執行個體的連線。 |
| 所有使用者端 | 連線成功，但Experience Manager Guides作業或結果無法使用。 | 確認已驗證的AEM帳戶具有必要的Experience Manager Guides許可權，並且帳戶可以使用請求的操作。 |
| 所有使用者端 | 使用者端在連線之前運作後要求驗證。 | 驗證工作階段可能已過期或存取權可能已撤銷。 再次使用AEM進行驗證。 |



