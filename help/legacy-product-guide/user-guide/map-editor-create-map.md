---
title: 建立地圖
description: 在AEM Guides中使用地圖編輯器建立地圖。 尋找根據對應範本建立對應檔案的步驟。
feature: Authoring, Map Editor
role: User
source-git-commit: fa07db6a9cb8d8f5b133258acd5647631b22e28a
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# 建立地圖 {#id176FEN0D05Z}

AEM Guides提供兩個現成可用的地圖範本 — DITA map和Bookmap。 您也可以建立自己的地圖範本，並與作者共用這些範本，以建立地圖檔案。

執行以下步驟來建立對應檔案：

1. 在Assets UI中，導覽至您要建立地圖檔案的位置。

1. 按一下&#x200B;**建立** \> **DITA Map**。

1. 在Blueprint頁面上，選取您要使用的對應範本型別，然後按一下[下一步]****。

   >[!NOTE]
   >
   > 在對應檔案中參照主題的方式取決於對應範本。 例如，如果您選取「對應」範本，則主題參照\(`topicref`\)會用來參照主題。 若是Bookmap，主題參考是使用DITA中的`chapter`元素所建立。

   ![](images/map-template.png){width="650" align="left"}

1. 在[屬性]頁面上，指定對應&#x200B;**標題**。

1. \（選用\）指定檔案&#x200B;**名稱**。

   如果管理員已根據UUID設定設定自動設定檔案名稱，則您將看不到指定檔案名稱的選項。 系統會自動為檔案指定以UUID為基礎的檔案名稱。

   如果檔案命名選項可用，也會根據您對映的標題自動建議名稱。 如果您要手動指定對應檔案名稱，請確定檔案名稱不含任何空格、單引號或大括弧，且結尾為`.ditamap`。

1. 按一下&#x200B;**建立**。

   便會顯示「已建立對應」訊息。

   您從Assets UI **建立** \> **DITA Map**&#x200B;或Web編輯器建立的每個新對應檔案都會被指派唯一的對應ID。 此外，新地圖也會儲存為DAM中的最新工作副本。 除非儲存新建立對映的修訂版本，否則您不會在「版本記錄」中看到任何版本號碼。 如果您開啟地圖進行編輯，版本資訊會顯示在地圖檔案之索引標籤的右上角：

   ![](images/first-version-map-none.png){width="650" align="left"}

   新建立的地圖的版本資訊顯示為&#x200B;*none*。 儲存新版本時，會為其指定版本編號1.0。如需有關儲存新版本的詳細資訊，請參閱[另存為新版本](web-editor-features.md#save-as-new-version-id209ME400GXA)。

   您可以選擇在設定的對應編輯器中開啟對應以進行編輯，或將對應檔案儲存在AEM存放庫中。

   >[!NOTE]
   >
   > 若要使用「進階對映編輯器」，請存取網頁編輯器中的對映檔案。 如果您的管理員已將「進階對應編輯器」設定為對應檔案中的預設編輯器，則對應檔案會直接在「進階對應編輯器」中開啟以進行編輯。 請參閱安裝和設定Adobe Experience Manager Guidesas a Cloud Service中的&#x200B;*將進階地圖編輯器設為預設值*&#x200B;區段。


**父級主題：**[&#x200B;使用對應編輯器](map-editor.md)
