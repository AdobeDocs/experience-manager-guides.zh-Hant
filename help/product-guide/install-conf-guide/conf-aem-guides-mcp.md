---
title: 搭配Adobe Experience Manager Guides使用MCP
description: 瞭解如何將模型上下文通訊協定(MCP)與AEM Guides搭配使用，以透過AI助理使用主題、地圖、基線和報告
feature: Authoring
role: User
source-git-commit: 864884f26389d256b0e054e3c0b7400b89f6d6ce
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%
---

# 使用Adobe Experience Manager Guides MCP伺服器

模型上下文通訊協定(MCP)是AI助理連線到外部工具和資料的標準方法，而不是您切換上下文以自己操作這些工具。

Adobe Experience Manager Guides MCP伺服器可將此連線至Experience Manager Guides。 它可讓啟用MCP的AI助理（例如Anthropic Claude）連線至您的Experience Manager Guides環境，並在您自己的AEM許可權下代表您行事。 連線後，您就可以在Experience Manager Guides as a Cloud Service上使用純自然語言的地圖、主題、基線和報表。

本文說明為什麼MCP對Experience Manager Guides有用、MCP伺服器涵蓋的範圍、使用中的應用程式以及如何使用。

## Experience Manager Guides的MCP為何有用

檔案團隊經常將大量時間花在重複的、需要大量導覽的工作上，例如在大型地圖中尋找主題、檢查檔案狀態、追蹤中斷的連結、建立版本的基準或匯出報表。 有了Experience Manager Guides MCP伺服器，您可以要求AI助理直接處理這些動作，無需切換至Experience Manager Guides UI。

例如：

- 不要開啟地圖並逐一檢查每個主題的狀態，請要求助理列出主題及其狀態。
- 與其手動啟動中斷連結報告並等候Experience Manager Guides UI，請要求助理執行報告並告知您報告執行完畢的時間。
- 請要求助理員為特定地圖建立基準線，而不是導覽至基準線畫面。

## Experience Manager Guides提供的MCP伺服器

Experience Manager Guides公開使用Experience Manager Guides內容和相關工作流程的MCP功能。 視您的AEM許可權而定，MCP伺服器會提供對下列功能的存取：

* **主題與對映**：在整個內容生命週期中處理主題與對映，從建立和檢視內容到更新、版本設定、鎖定和刪除內容。
* **基準線**：透過建立、列出、匯出、複製、重建及標示基準線來使用基準線。
  >[!NOTE]
  >
  > 對於Cloud Service和內部部署環境，基準線功能僅在啟用[新基準線](../user-guide/web-editor-baseline-v2.md)時可用。
* **報表**：存取主題清單和中繼資料、識別中斷的連結，以及檢閱多媒體使用方式，以深入瞭解您的內容。
* **系統**：透過檢查封裝版本、套件健康狀態和環境診斷，瞭解您的系統狀態。

如果您沒有在AEM中執行動作的許可權，則無法透過MCP執行相同的動作。

確切的可用工具可能會隨著時間而改變。 請要求您的助理顯示可用的專案，而非依賴固定清單：

`List all Experience Manager Guides tools available and describe what they do.`


## 支援的應用程式

Experience Manager Guides MCP伺服器是遠端MCP伺服器，可與相容的MCP使用者端連線。 根據您的環境，連線您的MCP使用者端並向Experience Manager Guides MCP伺服器驗證。 如需詳細資料，請檢視[設定Experience Manager Guides MCP伺服器](./configure-aem-guides-mcp.md)。

## 使用Experience Manager Guides MCP伺服器

連線後，以簡單的語言描述您想要的內容。 輔助程式會選取適當的刀具並填入其引數，例如對映路徑或基線名稱。

>[!IMPORTANT]
>
> 涉及多個步驟或需要一些時間才能完成的請求（例如匯出、基準線建置和大量更新），最適合用於思考模型。 這些會在背景執行：助理員會啟動工作，然後檢查其狀態，直到結果或下載連結準備就緒為止。

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


