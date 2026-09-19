---
title: Experience Manager Guides檔案
description: 尋找Adobe Experience Manager Guides的檔案。 瞭解Experience Manager中的原生DITA支援、結構化撰寫和多管道發佈。
feature: AEM Guides Tutorials
role: User
TQID: https://experienceleague.adobe.com/S4wTM-7gfU7D-JfKVbb9nK3qoQIG6PdiY7jtpsc6kDs
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
    internal-label: Authoring
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
  - id: d90290ec-3e61-4ebd-8649-bcafe0836803
    internal-label: Reports
  - id: f59890ff-de81-47d5-9ef8-7ab2dd10c6c3
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: aad65a09-20cc-4780-ad44-329d14dc8481
    internal-label: Workflows
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
    internal-label: Editor
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
    internal-label: Web Editor
  - id: f901afa4-5613-4581-add5-219fa5f03fb5
    internal-label: Publishing
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: f5c2a4bb-71ca-4d7e-8efd-442250e6ba48
    internal-label: Content reuse
source-git-commit: 411756129e6ce756f8674d6d3feb27a1cd9a2f19
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 5%
---
# Experience Manager Guides檔案

Experience Manager Guides是一款企業級CCMS，具備適用於結構化撰寫、多頻道發佈及內容生命週期管理的原生DITA支援。

**部署：** [!BADGE Cloud Service]{type=Positive} [!BADGE 內部部署]{type=Informative}

## 由您的角色開始

::::landing-cards-container
:::card
![管理員圖示](./user-guide/images/admin.png)

管理員

設定檔案夾設定檔、許可權、工作流程設定和輸出範本。

[管理指南](./install-conf-guide/introduction.md)
:::

:::card
![作者圖示](./user-guide/images/author.png)

作者

建立和管理DITA主題、地圖、內容重複使用和稽核工作流程。

[製作概觀](./user-guide/authoring-content.md)
:::

:::card
![發佈者圖示](./user-guide/images/publish.png)

發佈者

設定輸出預設集、管理基準線，以及跨通道產生輸出。

[地圖管理與發佈](./user-guide/map-console-overview.md)
:::

::::


<!--
:::card
![Architects icon](./user-guide/images/architect.svg)

Architects

Design DITA specializations, schemas, and content architecture for your implementation.

[DITA specialization](./install-conf-guide/dita-ot-specialization.md)
:::

::::
-->

## 依功能區域瀏覽

<!-- Author note: Six cards will wrap to two rows of three in production. Same beta caveat as the role cards above applies here. -->

::::landing-cards-container

:::card
![製作圖示](./user-guide/images/author.svg)

製作

網頁編輯器、FrameMaker整合、可重複使用的內容以及稽核週期。

[編寫您的內容](./user-guide/web-editor.md)
:::

:::card
![檢閱圖示](./user-guide/images/review.svg)

檢閱

稽核主題、管理稽核任務和稽核通知。

[評論簡介](./user-guide/review.md)
:::

:::card
![發佈圖示](./user-guide/images/publish.svg)

發佈

PDF、AEM Sites、HTML5、EPUB和JSON輸出型別。

[發佈您的內容](./user-guide/generate-output.md)
:::

:::card
![翻譯圖示](./user-guide/images/Smock_GlobeGrid_18_N.svg)

翻譯

多語言內容的人工和機器翻譯工作流程。

[翻譯內容](./user-guide/translation.md)
:::

:::card
![報告圖示](./user-guide/images/Smock_Report_18_N.svg)

報告

主題清單、多媒體、中斷的連結和中繼資料報表。

[產生報表](./user-guide/reports-intro.md)
:::

:::card
![設定圖示](./user-guide/images/config.svg)

設定

資料夾設定檔、DITA-OT自訂和輸出範本。

[設定資料夾設定檔](./install-conf-guide/conf-profiles.md)
:::

::::

## 新增功能

<!-- Author note: Badges render correctly in markdown table cells per ExL spec. <br> is supported within cells. Update release version, links, and descriptions each release cycle. The What's new table is the primary update touchpoint on this page — aim to refresh it within one week of each cloud service release. -->
::::landing-cards-container

:::card
![系統管理員圖示](https://cdn.experienceleague.adobe.com/icons/admin.svg)

Git聯結器

直接從Git存放庫將內容匯入指南中。

[使用Git聯結器匯入內容](./user-guide/web-editor-git-connector.md)
:::

:::card
![疑難排解圖示](https://cdn.experienceleague.adobe.com/icons/atomic-search-troubleshoot.svg)

新地圖集合

用於管理地圖和發佈輸出的統一介面。

[新地圖集合](./user-guide/web-editor-git-connector.md)
:::

:::card
![書本圖示](https://cdn.experienceleague.adobe.com/icons/book.svg)

委派稽核任務

稽核者可以將稽核任務委派給其他稽核者。

[委派稽核任務](./user-guide/review-complete-review-tasks.md#delegate-a-review-task-to-another-reviewer)
:::

::::

<!--
<table>
<tr>
<td>

[!BADGE Feature]{type=Neutral} <br> [**Import content using Git Connector**](./user-guide/web-editor-git-connector.md)<br> Import content into Guides directly from Git repositories.

</td>
<td>

[!BADGE Feature]{type=Neutral} <br> [**New map collection**](./user-guide/generate-output-use-new-map-collection-output-generation.md)<br> Unified interface for managing maps and publishing outputs

</td>
<td>

[!BADGE Enhancement]{type=Neutral} <br> [**Delegate a review task**](./user-guide/review-complete-review-tasks.md#delegate-a-review-task-to-another-reviewer) <br> Reviewers can delegate a review task to another reviewer

</td>
</tr>
</table>
-->


## 其他資源

* [Cloud Service發行說明](./release-info/latest-release-info-cs.md)
* [On-Premise版本注意事項](./release-info/latest-release-info.md)
* [AEM Guides社群](https://experienceleaguecommunities.adobe.com/adobe-experience-manager-guides-11){target="_blank"}
* [GitHub存放庫](https://github.com/AdobeDocs/experience-manager-guides.en){target="_blank"}
* [支援](https://experienceleague.adobe.com/support/v2/en/){target="_blank"}
* [教學影片](https://experienceleague.adobe.com/en/docs/experience-manager-guides-learn/videos/getting-started/overview){target="_blank"}
