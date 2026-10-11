---
title: 如何將[!DNL Experience Manager Guides]新增至您的[!DNL Experience Manager as a Cloud Service]環境
description: 瞭解如何將[!DNL AEM Guides]新增至您的[!DNL AEM as a Cloud Service]環境
exl-id: a1e020c2-360c-4d71-b5fd-8179d9ceacda
feature: Installation
role: Leader
TQID: 'https://experienceleague.adobe.com/lb5mjLR6M3pdFlsdQpwGXotEhbPeyetJ4zVwKV-J-Yg'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
  - id: e557051c-ff02-4ff8-9421-cf452af0edd5
    internal-label: Installation
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%
---
# [!DNL Adobe Experience Manager Guides] as a Cloud Service部署

瞭解如何將[!DNL Experience Manager Guides]新增至您的[!DNL Experience Manager as a Cloud Service]環境。


>[!NOTE]
>
> 從2024.2.0版開始，Experience Manager Guides僅能作為Experience Manager as a Cloud Service的自動化附加元件提供。 如果您使用Experience Manager Guides的手動部署，請在為程式啟用Experience Manager Guides之前，先移除雲端管理Git程式碼基底中的第`<module>dox.installer</module> from file dox/pom.xml`行。

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
