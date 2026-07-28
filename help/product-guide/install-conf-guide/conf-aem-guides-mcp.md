---
title: 搭配Adobe Experience Manager Guides使用MCP
description: 瞭解如何將模型上下文通訊協定(MCP)與AEM Guides搭配使用，以透過AI助理使用主題、地圖、基線和報告
feature: Authoring, Publishing
role: User
source-git-commit: c724946a3426e28a1270ba01cdf2646bbf5f2a0d
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 0%

---


# 使用Adobe Experience Manager Guides MCP伺服器

模型上下文通訊協定(MCP)是AI助理連線到外部工具和資料的標準方法，而不是您切換上下文以自己操作這些工具。

Adobe Experience Manager Guides MCP伺服器可將此連線至Experience Manager Guides。 它可讓啟用MCP的AI助理（例如Anthropic Claude）連線至您的Experience Manager Guides環境，並在您自己的AEM許可權下代表您行事。 連線後，您就可以在Experience Manager Guides as a Cloud Service上使用純自然語言的地圖、主題、基線和報表。

本文說明為什麼MCP對Experience Manager Guides很有用、MCP伺服器涵蓋什麼、它使用哪些應用程式、如何設定以及如何使用。

## Experience Manager Guides的MCP為何有用

檔案團隊經常將大量時間花在重複的、需要大量導覽的工作上，例如在大型地圖中尋找主題、檢查檔案狀態、追蹤中斷的連結、建立版本的基準或匯出報表。 有了Experience Manager Guides MCP伺服器，您可以要求AI助理直接處理這些動作，無需切換至Experience Manager Guides UI。

例如：

- 不要開啟地圖並逐一檢查每個主題的狀態，請要求助理列出主題及其狀態。
- 與其手動啟動中斷連結報告並等候Experience Manager Guides UI，請要求助理執行報告並告知您報告執行完畢的時間。
- 請要求助理員為特定地圖建立基準線，而不是導覽至基準線畫面。

## Experience Manager Guides提供的MCP伺服器

Experience Manager Guides透過單一HTTP端點公開其MCP功能。

| MCP伺服器 | 端點 | 說明 |
| --- | --- | --- |
| **Experience Manager Guides** | `https://mcp.adobeaemcloud.com/adobe/mcp/guides` | 在Experience Manager Guides中使用主題與地圖、基準線與報表。 |

這個端點涵蓋四個區域：

- **主題與地圖** — 建立、讀取、更新、刪除、版本及鎖定主題與地圖。
- **基準線** — 建立、列出、匯出、複製、重新建置和標籤基準線。
- **報表** — 主題清單、中繼資料、中斷的連結及多媒體使用。
- **系統** — 封裝版本、套件組合健康狀態和環境診斷。

確切的可用工具可能會隨著時間而改變。 請要求您的助理顯示可用的專案，而非依賴固定清單：

```
List all Experience Manager Guides tools available from the author https://author-pXXXX-eXXXX.adobeaemcloud.com and describe what they do.
```

## 為您的組織要求存取權

存取Experience Manager Guides MCP伺服器的許可權是每個組織&#x200B;**選擇加入**。 在您組織中的任何人能夠連線之前：

- 必須在您的AEM as a Cloud Service環境中啟用Experience Manager Guides 。
- 貴組織的IMS組織ID （組織ID）必須由Adobe Guides團隊加入允許清單。

若要請求存取權，請聯絡您的Adobe客戶成功團隊。

## 支援的應用程式

Experience Manager Guides MCP伺服器是&#x200B;**遠端**&#x200B;伺服器。 它可與任何支援遠端伺服器的MCP使用者端搭配使用，包括：

### 聊天應用程式

- Anthropic Claude （網頁與案頭）

### 開發人員工具

- 游標
- Visual Studio Code
- 其他支援MCP的IDE

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

## 驗證

Experience Manager Guides MCP伺服器使用&#x200B;**Adobe IMS**&#x200B;進行驗證。

- 初次連線時，您的使用者端會開啟瀏覽器登入視窗。 使用您的Adobe ID登入以完成連線。
- 登入後，每個動作都會在現有的AEM許可權下執行。 如果您沒有AEM中動作的許可權，則相同的動作會透過MCP失敗。

## 使用Experience Manager Guides MCP伺服器

連線後，以簡單的語言描述您想要的內容。 輔助程式會選取適當的刀具並填入其引數，例如對映路徑或基線名稱。

>[!IMPORTANT]
>
>涉及多個步驟或需要一些時間才能完成的請求（例如匯出、基準線建置和大量更新），最適合用於思考模型。 這些會在背景執行：助理員會啟動工作，然後檢查其狀態，直到結果或下載連結準備就緒為止。

### 提示範例

以下提示說明典型請求，每個請求都會觸發不同的工具：

1. **檢查地圖中的主題狀態**

   > 在`/content/dam/docs/user-guide.ditamap`列出地圖中的所有主題，並顯示其標題和檔案狀態。

1. **建立基準線**

   > 建立標題為「版本3.2」的`/content/dam/docs/user-guide.ditamap`靜態基準線。

1. **執行報告**

   > 執行使用手冊的中斷連結報告，並在準備就緒時提供下載連結。

## 期望管理

- **驗證結果** — 助理可能會犯錯誤，例如選擇錯誤的地圖或主題。 在使用報告或新基準線之前，請先檢閱報告。
- **它會隨著時間而改善** — 隨著助理越來越好，今天需要幾個提示的工作可能會稍後需要一個提示。
- **您仍然進行通話** — 助理可以告訴您主題的狀態或列出中斷的連結，但是決定內容是否準備發佈仍由檢閱者或發佈者決定。
- **自動核準時請小心** — 有些MCP使用者端（包括Claude）會讓您自動核准動作，而非確認每個動作。 唯讀動作（例如執行報表）可接受此設定。 對於建立、變更或鎖定內容的動作，請確認每個動作，以便您可以在動作生效前加以檢閱。

如需Experience Manager Guides MCP的相關問題，請聯絡您的Adobe客戶成功團隊。


