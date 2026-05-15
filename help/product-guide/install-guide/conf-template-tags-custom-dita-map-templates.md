---
title: 設定自訂DITA map範本
description: 瞭解如何設定自訂DITA map範本
exl-id: ea8a6687-1a7b-45c7-8cbc-161f9e88a8be
feature: Template Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/16cGf5xY2tAfhc0qIBZeUhYTes-RrdRp-Kj-MoTuacE
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: a7bba4a6-624b-4427-a9b8-dd411a1bfd41id: ad602516-aca3-4247-9ae8-f393d958efa9id: df6fa66f-4542-4a6d-90ca-9f146eb5d494
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 1%

---

# 設定自訂DITA map範本 {#id1774F04F05Z}

AEM Guides隨附兩個現成可用的地圖範本 — DITA map和Bookmap。 您可以根據這些範本建立對映；或者，您可以定義自己的對映範本，然後使用這些範本建立新的對映。

執行以下步驟以新增自訂地圖範本：

1. 以管理員身分登入Adobe Experience Manager。

1. 在Assets UI中，導覽至設定用來儲存地圖範本檔案的資料夾。 依預設，所有對應範本都會儲存在/content/dam/dita-templates/maps資料夾中。

   >[!NOTE]
   >
   > 若要設定自訂位置以儲存主題或對應範本，請參閱[設定自訂DITA範本資料夾路徑](conf-template-tags-custom-dita-topic-template.md#id191LCF0095Z)

1. 按一下&#x200B;**建立** \> **DITA範本**。

1. 在Blueprint頁面上，選取您要建立的對映範本型別。

   >[!NOTE]
   >
   > 您可以使用Map或Bookmap範本作為新範本的基礎。

1. 按一下「**下一步**」。

1. 在新範本[內容]頁面上，輸入範本的&#x200B;**Title**&#x200B;和&#x200B;**Name**。

   >[!NOTE]
   >
   > 系統會根據範本的標題自動建議名稱。 如果您要手動指定名稱，請確定名稱不含任何空格、單引號或大括弧，且結尾為.ditamap。

1. 按一下「**建立**」。

   便會顯示「已建立對應」訊息。

   您可以選擇在「對映編輯器」中開啟範本以進行編輯，或將範本檔案儲存在範本存放區位置。 建立範本後，您就可以根據編寫需求，使用地圖編輯器來自訂範本。 設定好範本後，請確定您將其與全域或資料夾層級的設定檔建立關聯。


下次建立新地圖時，您的範本會顯示在Blueprint頁面中。 如需有關建立DITA map的詳細資訊，請參閱&#x200B;*使用Adobe Experience Manager Guides*。

>[!TIP]
>
> 如需使用自訂對應範本的最佳實務，請參閱「最佳實作指南」中的&#x200B;*自訂範本*&#x200B;區段。

**父級主題：** [設定主題與對應範本](conf-template-tags.md)
