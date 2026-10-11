---
title: 部署和Dispatcher設定
description: 瞭解Experience Manager Guides as a Cloud Service中的部署和Dispatcher設定
feature: Introduction, Installation
role: Admin
level: Experienced
exl-id: 657a42be-36e7-4657-83d5-e866f8e55f09
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
  - id: c5fd2af0-6cbb-4746-ab0d-40ecb093af12
    internal-label: Introduction
  - id: e557051c-ff02-4ff8-9421-cf452af0edd5
    internal-label: Installation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 6%
---
# 部署和Dispatcher設定

本文提供如何部署Experience Manager Guides as a Cloud Service和設定Dispatcher的相關資訊。

## 部署Experience Manager Guides as a Cloud Service

您可以透過Cloud Manager部署Experience Manager Guides來開始進行。 若要部署模組，請依照[AEM Guides as a Cloud Service部署](../release-info/deploy-xml-on-aemaacs.md)中所述的指示進行。

>[!NOTE]
>
> 從2024.2.0版開始，Experience Manager Guides僅能作為Experience Manager as a Cloud Service的自動化附加元件提供。 如果您使用2023年12月或較舊版本，可以從GitHub存放庫下載Adobe Experience Manager Guides並進行安裝。 如果您使用Experience Manager Guides的手動部署，請在為程式啟用Experience Manager Guides之前，移除雲端管理Git程式碼基底中的第`<module>dox.installer</module> from file dox/pom.xml`行。

執行以下步驟來部署Experience Manager Guides模組：

1. 登入[!UICONTROL Cloud Manager]。

1. 編輯您要設定[!DNL Experience Manager Guides]的方案。

1. 切換到&#x200B;**[!UICONTROL 解決方案和附加元件]**&#x200B;索引標籤。

1. 在&#x200B;**[!UICONTROL 解決方案和附加元件]**&#x200B;資料表中，按一下&#x200B;**[!UICONTROL Assets]**。

1. 選取&#x200B;**[!UICONTROL 參考線]**&#x200B;並選取&#x200B;**[!UICONTROL 儲存]**。

您已成功設定程式以自動布建Experience Manager Guides解決方案。

![設定Experience Manager Guides解決方案](assets/addon-configuration.png)

>[!NOTE]
>
>若要在整合程式下的任何環境中安裝[!DNL Experience Manager Guides]，您必須執行與環境關聯的管道。 在您的CM Git程式碼基底中不需要額外的設定，即可安裝[!DNL Experience Manager Guides]。


## 設定Dispatcher

Dispatcher 是 Adobe Experience Manager 的快取和/或負載平衡工具。 如需詳細資訊，請參閱[雲端中的Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=zh-Hant)。

1. 若要將Dispatcher設定從AMS移轉至Cloud Service，請參閱[將Dispatcher設定從AMS移轉至AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/ams-aem.html?lang=zh-Hant)。
1. 如需有關如何設定Dispatcher的詳細資訊，請參閱[設定Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=zh-Hant)。

>[!NOTE]
>
> AEM as a Cloud Service不支援用於製作例項的Dispatcher。
