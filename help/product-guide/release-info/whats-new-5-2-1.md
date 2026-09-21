---
title: 發行說明 | Adobe Experience Manager Guides 5.2.0 Service Pack 1版的新增功能
description: 瞭解Adobe Experience Manager Guides 5.2.0 Service Pack 1版中的新功能和增強功能
role: Leader
TQID: https://experienceleague.adobe.com/dXXQ1YvVduT11vvF5qyXHLqnuo1xMKkAb5I-EoD2JAA
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
source-git-commit: 788d0b9a2e2f07d2990bcc4f984f3ba4a4aabf17
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%
---
# 5.2.0 Service Pack 1版（2026年9月）的新增功能

本文介紹5.2.0 Service Pack 1版Adobe Experience Manager Guides推出的新功能和增強功能。

如需此版本中已修正的問題清單，請檢視5.2.0 Service Pack 1版本[&#128279;](fixed-issues-5-2-0-sp1.md)中的已修正問題。

瞭解5.2.0 Service Pack 1版本[&#128279;](../release-info/upgrade-instructions-5-2-0-sp1.md)的升級指示。


## Experience Manager Guides新增MCP支援

Experience Manager Guides現在支援模型內容通訊協定(MCP)。 您可以將Claude、Cursor等AI工具連線到Guides，而無需任何自訂工作。 透過單一MCP端點，在這個版本中，已驗證身分的使用者可以將Guides用作Headless系統，並管理主題和地圖、建立和匯出基準線，以及產生報表，同時都在他們現有的AEM許可權下操作。 這使檔案團隊能夠使用AI應用計畫和代理程式更高效地工作。

如需詳細資訊，請檢視[使用Adobe Experience Manager Guides MCP伺服器](../install-conf-guide/conf-aem-guides-mcp.md)。


## 新編輯器中現在支援外部資料來源和引文

新編輯器現在支援兩種現有的Experience Manager Guides功能：與外部資料來源連線以及在檔案中使用引文的功能。

在新的編輯器中建立或更新內容時，作者可以繼續使用已設定的外部資料來源。 也支援引用，讓作者無需切換編輯器，即可新增及管理內容中的引用。

## 支援AMA引文樣式

Experience Manager Guides現在支援美國醫學協會(AMA)的引文風格，將現有的引文架構加以擴充，以符合醫療保健、法規及生命科學等行業的客戶所要求的檔案標準。

在&#x200B;**Workspace設定**&#x200B;中選取AMA作為引文樣式時，引文會根據AMA准則自動格式化，包括數字上標轉譯、循序編號和精確的參考清單排序。 在選取AMA時，編輯器中只能使用&#x200B;**剖析引文**&#x200B;選項，讓作者可以新增及剖析引文，而不需切換內容。

原生PDF和AEM Sites輸出格式支援AMA引文樣式。 若要設定引文樣式，請移至&#x200B;**Workspace設定**，然後從引文樣式選項中選取AMA。 如需詳細資訊，請檢視[使用引文](../user-guide/web-editor-apply-citations.md)。


