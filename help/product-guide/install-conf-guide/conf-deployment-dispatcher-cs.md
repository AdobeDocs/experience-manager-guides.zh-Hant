---
title: 部署和Dispatcher設定
description: 瞭解Experience Manager Guides as a Cloud Service中的部署和Dispatcher設定
feature: Introduction, Installation
role: Admin
level: Experienced
source-git-commit: 834959a6a0e22cd5d2b2c5d0e57ceb6d45c0c666
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 3%

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

Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。如需詳細資訊，請參閱[雲端中的Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en)。

1. 若要將Dispatcher設定從AMS移轉至Cloud Service，請參閱[將Dispatcher設定從AMS移轉至AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/ams-aem.html?lang=en)。
1. 如需有關如何設定Dispatcher的詳細資訊，請參閱[設定Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=zh-Hant)。

>[!NOTE]
>
> AEM as a Cloud Service不支援用於製作例項的Dispatcher。
