---
title: 建立主題
description: 瞭解如何在AEM Guides的網頁編輯器中使用自訂範本來建立DITA主題型別。
exl-id: 84e9cfdf-e188-487f-9181-68708029c101
feature: Authoring
role: User
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# 建立主題 {#id2056AL00O5Z}

AEM Guides可讓您建立以下型別的DITA主題：主題、工作、概念、參照、字彙表、DITAVAL等等。 除了根據現成可用的範本建立主題外，您也可以定義自訂範本。 這些範本必須新增到資料夾設定檔，才能顯示在範本選擇Blueprint和網頁編輯器中。

請注意，全域和資料夾設定檔組態僅供資料夾層級管理使用者使用。 如需設定全域和資料夾層級設定檔的詳細資訊，請參閱安裝中的&#x200B;*設定撰寫範本*，並為您的設定設定Adobe Experience Manager Guides。

執行以下步驟來建立主題：

1. 在Assets UI中，導覽至您要建立主題的位置。

1. 若要建立新主題，請按一下&#x200B;**建立** \> **DITA主題**。

1. 在Blueprint頁面上，選取您要建立的DITA檔案型別，然後按一下&#x200B;**下一步**。

   ![](images/create_dita_topic.png){width="800" align="left"}

   依預設，AEM Guides提供最常用的DITA主題範本。 您可以根據組織需求設定更多主題範本，請參閱安裝中的&#x200B;*設定撰寫範本*，並為您的設定設定Adobe Experience Manager Guides。

   >[!NOTE]
   >
   > 在Assets UI的清單檢視中，DITA主題型別會在「型別」欄中顯示為「主題」、「任務」、「概念」、「參照」、「Glossentry」或「DITAVAL」。 DITA map會顯示為Map。

1. 在[內容]頁面上，指定檔案&#x200B;**標題**。

1. \（選用\）指定檔案&#x200B;**名稱**。

   如果管理員已根據UUID設定設定自動設定檔案名稱，則您將看不到指定檔案名稱的選項。 系統會自動為檔案指定以UUID為基礎的檔案名稱。

   如果檔案命名選項可用，也會根據檔案的&#x200B;**標題**&#x200B;自動建議名稱。 如果您要手動指定檔名稱，請確定&#x200B;**名稱**&#x200B;不含任何空格、單引號或大括弧，且結尾為.xml或.dita。 依預設，AEM Guides會以連字型大小取代所有特殊字元。 如需命名DITA檔案的最佳作法，請參閱最佳作法指南中的檔案名稱一節。

1. 按一下「**建立**」。「主題已建立」訊息便會顯示。

   您可以選擇在Web編輯器中開啟要編輯的主題，或將主題檔案儲存在AEM存放庫中。

   您從Assets UI **建立** \> **DITA主題**&#x200B;或Web編輯器建立的每個新主題都會指派唯一的主題ID。 此ID的值是檔案名稱本身。 此外，新檔案會儲存為DAM中主題的最新工作副本。 儲存新建立主題的修訂版本之前，您不會在「版本記錄」中看到任何版本號碼。 如果您開啟主題進行編輯，版本資訊會顯示在主題檔案之索引標籤的右上角：

   ![](images/topic-version-none_cs.png){width="550" align="left"}

   新建立之主題的版本資訊顯示為&#x200B;*none*。 儲存新版本時，會為其指定版本編號1.0。如需有關儲存新版本的詳細資訊，請參閱[另存為新版本](web-editor-features.md#save-as-new-version-id209ME400GXA)。


>[!NOTE]
>
> 如果您的管理員已將網頁編輯器設定為在編輯之前取出檔案，則您將無法編輯檔案，直到您取出檔案為止。 同樣地，如果已設定，系統會在關閉檔案前，要求您簽入任何已簽出的檔案。

>[!IMPORTANT]
>
> 建立DITA主題後，請繼續儲存對工作副本所做的變更，並在完成主題更新後建立新版本。

**父級主題：**[&#x200B;建立和預覽主題](create-preview-topics.md)
