---
title: Experience Manager Guides發行版本中的API更新
description: 瞭解Experience Manager Guides版本中的各種API更新
source-git-commit: 24637376024107ae575620e5491c0150da6cc956
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 2%

---


# Experience Manager Guides發行版本中的API更新

本文提供Adobe Experience Manager Guides發行之Swagger檔案中新增API的詳細資訊。 您可以導覽至&#x200B;**工具** > **指南** > **API Swagger**，透過AEM介面存取Swagger檔案。

<table style="border: 1; border-collapse: collapse; table-layout:fixed">
    <tr>
        <td colspan="5"><strong>2026.08.0版</strong></td>
    </tr>
    <tr>
        <td>功能</td>
        <td>子功能</td>
        <td>方法</td>
        <td>API</td>
        <td>描述</td>
    </tr>
    <tr>
        <td rowspan="7"><b>Assets</b></td>
        <td rowspan="7"></td>
        <td>POST</td>
        <td>'/bin/guides/v1/asset/import'</td>
        <td>將一個或多個資產匯入目標資料夾；支援多部分上傳和衝突解決</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/asset/list'</td>
        <td>傳回資料夾路徑下的資產分頁清單</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/asset/validatexml'</td>
        <td>驗證DITA XML的格式正確、結構描述有效性和參照完整性</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/asset/version/revert'</td>
        <td>將資產還原為指定版本</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/asset/currentversion/detail'</td>
        <td>傳回目前版本詳細資料（版本名稱、已變更狀態、標籤等）</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/assets/status'</td>
        <td>啟動非同步工作以檢查指定路徑下資產的參考線狀態</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/assets/status'</td>
        <td>按工作ID擷取資產狀態工作的狀態/結果</td>
    </tr>
    <tr>
        <td rowspan="3"><b>發佈</b></td>
        <td rowspan="3"></td>
        <td>POST</td>
        <td>'/bin/guides/v1/output/generate'</td>
        <td>開始執行預設集以產生地圖的輸出</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/output/status'</td>
        <td>依對應路徑和產生ID傳回單一輸出產生的狀態</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/output/status/list'</td>
        <td>傳回對應路徑所有已產生預設集的狀態</td>
    </tr>
    <tr>
        <td rowspan="18"><b>翻譯</b></td>
        <td rowspan="6">語言</td>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/language/copies'</td>
        <td>依路徑或UUID區分的資產語言副本</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/language/groups'</td>
        <td>資料夾設定檔的語言群組</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/language/list'</td>
        <td>支援翻譯語言（已篩選）</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/language/root'</td>
        <td>資產路徑可用的根語言</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/language/variable'</td>
        <td>依型別和語言程式碼區分的語言變數</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/language/variable'</td>
        <td>建立、更新或刪除語言變數</td>
    </tr>
    <tr>
        <td rowspan="7">專案</td>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/project/create'</td>
        <td>建立/更新DITA map的翻譯專案</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/project/sync'</td>
        <td>建立/更新翻譯專案（同步流程）</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/project/creationstatus'</td>
        <td>依路徑區分專案的翻譯同步狀態</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/project/existing'</td>
        <td>目前使用者的現有翻譯專案</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/project/inprogress'</td>
        <td>指定資產的進行中專案</td>
    </tr>
    <tr>
        <td>刪除</td>
        <td>'/bin/guides/v1/translation/project/delete'</td>
        <td>資產翻譯狀態/屬性的刪除前更新</td>
    </tr>
    <tr>
        <td>刪除</td>
        <td>'/bin/guides/v1/translation/project/job/delete'</td>
        <td>工作移除前的資產狀態刪除前更新</td>
    </tr>
    <tr>
        <td rowspan="5">參照</td>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/reference/accept'</td>
        <td>接受工作子頁面的翻譯內容</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/reference/reject'</td>
        <td>拒絕工作子頁面的翻譯內容</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/reference/sync'</td>
        <td>在目標資料夾中建立語言副本</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/reference/baseline/export'</td>
        <td>將翻譯基準匯出至目的地語言</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/reference/status/forcesync'</td>
        <td>強制將不同步的資產更新為不同步</td>
    </tr>
</table>
