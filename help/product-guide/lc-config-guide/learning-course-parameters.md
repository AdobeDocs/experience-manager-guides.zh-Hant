---
title: 學習者進度和課程完成的SCORM關鍵量度
description: 瞭解學習者進度和課程完成的SCORM關鍵量度
feature: Authoring
role: Admin
level: Experienced
source-git-commit: 0dff380131dadc971f257eb464700392328164e5
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 1%

---

# 學習者進度和課程完成的SCORM關鍵量度

本文列出了SCORM套件中擷取的主要引數，以及其對應的欄位和範例。 這些引數可提供學習者進度、課程完成、互動詳細資料和測驗成績的關鍵見解。 管理員可使用此資訊來驗證追蹤、設定報表，以及確保LMS環境內的分析準確無誤。 以下是每個引數在SCORM套件中顯示的範例值。

| **引數名稱** | **說明** | **欄位** | **範例** |
|---|---|---|---|
| **課程完成狀態** | 表示課程是否完成 | cmi.completion_status | 不完整 |
| **次嘗試計數** | 學習者嘗試的次數 | LMS端嘗試計數器/內容 | 嘗試： 1 |
| **SCORM封裝的位置** | 課程中的目前書籤或位置 | cmi.location | - |
| **進度完成** | 學習者的進度 | cmi.progress_measure | 0.87 |
| **總時間（嘗試）** | 目前嘗試的總逗留時間 | cmi.total_time | 0000:01:09.87 |
| **目錄可見度和主題計數** | 顯示TOC可見度和主題完成詳細資訊 | Project.HideTOC， Project.TotalTopics， Project.TopicsCompleted | - |
| **每個主題狀態** | 每個主題的完成和通過狀態 | 每個課程的自訂狀態 | - |
| **每個問題選擇狀態** | 追蹤學習者針對每個問題所選取的選擇 | 值， generated_id，已核取 | - |
| **整體問題分數** | 在問題層級取得的分數和彙總 | {&quot;score&quot;:0，&quot;maxScore&quot;:1}和% | &quot;score&quot;:33.33，&quot;maxScore&quot;:100，&quot;minScore&quot;:0 |
| 每個問題層級&#x200B;**互動** | 每個問題的學習者互動細節 | id/type/timestamp/correct_response/learner_response/result/latency | - |
| **整體課程狀態** | 表示通過/失敗和整體進度 | success_status， completion_status， score， progress_measure | 通過還是失敗 |
| **學習者詳細資料** | 依ID和名稱識別學習者 | cmi.learner_id， cmi.learner_name | Albert |
| **測驗引數** | 測驗時間與及格分數設定 | cmi.max_time_allowed， cmi.scaled_passing_score， cmi.time_limit_action | 未定義或設定的值 |