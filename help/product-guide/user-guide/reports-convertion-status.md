---
title: 轉換狀態報表
description: 在AEM Guides中將不同格式的檔案轉換為DITA。 瞭解如何新增篩選器並檢視轉換狀態報告。
exl-id: 0a4699e5-865f-40e1-a17f-5e1a248ea955
feature: Report Generation
role: User
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 轉換狀態報表 {#id205BBA00WZZ}

AEM Guides提供強大的轉換功能，可將各種格式的檔案轉換成DITA。 「轉換狀態報表」提供AEM Guides所執行之所有轉換工作的整合檢視。

執行下列步驟以檢視「轉換狀態報表」：

1. 按一下頂端的Adobe Experience Manager連結，然後選擇 **工具**.

1. 選取 **指南** 工具清單中。

1. 按一下 **轉換狀態報表** 圖磚。

   系統會針對系統上執行的所有轉換工作，顯示「轉換狀態報告」。

   ![](images/conversion-status-report.png){width="800" align="left"}

1. 報告頁面分為兩個部分：

   - **篩選：**

     您可以根據「檔案型別」和「轉換狀態」來篩選報表資料。 在「檔案型別」中，您可以選擇檢視Word檔案、結構化HTML、XML和DocBook檔案型別的報表資料。 在「狀態」中，您可以選擇檢視已成功執行、失敗、作用中或佇列之工作的報表資料。

     下列熒幕擷圖顯示處於「失敗」、「作用中」和「已排入佇列」狀態的轉換工作的報表資料。

     ![](images/conversion-report-failed-active-queued.png){width="800" align="left"}

   - **報表資料：**

     報表資料包含以下欄：

      - **檔案名稱**：執行轉換程式之來源檔案的名稱。 按一下「檔案名稱」連結，即可前往來原始檔位置。

      - **檔案型別**：來原始檔的型別，可以是Word、結構化HTML、XML和DocBook。

      - **新增者**：執行轉換任務的使用者名稱。

      - **新增日期**：執行任務的日期。 按一下「新增日期」連結，即可下載記錄檔。

      - **路徑**：來原始檔的完整路徑。

      - **狀態**：轉換任務的狀態 — 「成功」、「失敗」、「作用中」或「已排入佇列」。

      - **輸出**：成功轉換檔案的路徑。 按一下「輸出」連結，即可前往儲存輸出的位置。


**父級主題：**[&#x200B;報表](reports-intro.md)
