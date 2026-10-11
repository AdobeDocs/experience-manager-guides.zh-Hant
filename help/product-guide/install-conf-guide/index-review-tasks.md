---
title: 執行索引以在「註釋」面板中包含所有稽核任務
description: 瞭解如何為現有的稽核任務建立索引，使其與較新的任務一起顯示在評論面板的稽核任務下拉式清單中。
feature: Web Editor Configuration
role: Admin
level: Experienced
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
    internal-label: Web Editor configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%
---
# 執行索引以將主題的所有稽核任務包含在「註解」面板中

「註解」面板中可用的「檢視主題[&#128279;](../user-guide/review-address-review-comments.md#view-all-review-tasks-for-a-topic)」功能的檢視所有稽核任務，可讓作者選取與目前開啟的主題相關聯的任何稽核任務（開啟或關閉），而不需切換稽核專案。 啟用時，編輯器中的&#x200B;**註解**&#x200B;面板會包含下拉式清單，列出主題所屬的每個稽核任務，以及每個任務的狀態及其所屬的專案。

依預設，在執行個體上啟用此功能時，複查工作會在建立時編列索引，因此它們會自動在此下拉式清單中使用。

但是，如果在執行個體上部署Experience Manager Guides時停用該功能，則在其保持停用狀態時建立的稽核任務不會編制索引。 作為管理員，如果您在已經存在此類稽核任務之後啟用該功能，則這些任務在編制索引之前不會出現在下拉式清單中。 若要使其可用，您必須執行一次性指令碼，為現有的稽核工作編制索引。

執行下列cURL命令一次，為現有的稽核工作編制索引：

```bash
curl --location 'http://<host>:<port>/bin/guides/script/start' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Basic <base64-encoded-credentials>' \
--header 'Cookie: cq-authoring-mode=TOUCH' \
--data-urlencode 'jobType=review-topic-guids-migration'
```
