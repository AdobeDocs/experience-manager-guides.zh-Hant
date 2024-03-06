---
title: 如何新增 [!DNL Experience Manager Guides] 至您的 [!DNL Experience Manager as a Cloud Service] 環境
description: 瞭解如何新增 [!DNL AEM Guides] 至您的 [!DNL AEM as a Cloud Service] 環境
exl-id: a1e020c2-360c-4d71-b5fd-8179d9ceacda
feature: Installation
role: Leader
source-git-commit: 1b25f1df67fa2442ab79830dc2ac5a6eabd0394c
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager Guides] as a Cloud Service部署

瞭解如何新增 [!DNL Experience Manager Guides] 至您的 [!DNL Experience Manager as a Cloud Service] 環境。


>[!NOTE]
>
> 從2024.2.0版開始，Experience Manager指南僅以Experience Manageras a Cloud Service的自動化附加元件形式提供。 如果您對Experience Manager指南使用手動部署，請移除此行 `<module>dox.installer</module> from file dox/pom.xml` 在您的雲端管理Git程式碼基底中，再啟用程式的Experience Manager指南。

1. 登入 [!UICONTROL Cloud Manager].

1. 編輯要設定的程式 [!DNL Experience Manager Guides].

1. 切換至 **[!UICONTROL 解決方案和附加元件]** 標籤。

1. 在 **[!UICONTROL 解決方案和附加元件]** 表格，按一下 **[!UICONTROL 資產]**.

1. 選取 **[!UICONTROL 指南]** 並選取 **[!UICONTROL 儲存]**.

您已成功設定程式以自動布建Experience Manager指南解決方案。

![設定Experience Manager Guides解決方案](assets/addon-configuration.png)

>[!NOTE]
>
>若要安裝 [!DNL Experience Manager Guides] 在整合計畫下的任何環境中，您必須執行與環境關聯的管道。 您的CM Git程式碼基底中不需要進行額外的設定即可安裝 [!DNL Experience Manager Guides].
