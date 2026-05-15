---
title: 管理全域和資料夾設定檔輸出預設集
description: 瞭解如何在AEM Guides中以管理使用者的身分建立、編輯、重新命名、複製和刪除全域和資料夾設定檔輸出預設集。
feature: Authoring, Features of Web Editor, Publishing
role: User
hide: true
exl-id: 4e9cd1d5-1c28-4363-917d-f58511c4f809
TQID: https://experienceleague.adobe.com/KH-j3haVf3VmR0QpMgAOCFfdJoCUOuc-nx5Xrc2XTKI
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 420
ht-degree: 0%

---

# 管理全域和資料夾設定檔輸出預設集 {#id22BLJ0D0V1U}

全域和資料夾設定檔預設集僅適用於資料夾層級的管理使用者。

身為管理員，AEM Guides可讓您建立並管理全域和資料夾設定檔的輸出預設集。 然後，您就可以輕鬆地使用這些輸出預設集，為與該全域或資料夾設定檔相關的所有地圖產生輸出。

執行以下步驟，為「全域設定檔」和「資料夾設定檔」建立輸出預設集：

1. 選取要為其建立輸出預設集的DITA map。
1. 從對應檔的&#x200B;**選項**&#x200B;功能表選取&#x200B;**編輯主題**&#x200B;選項。 會開啟對應檔案，以便在Web編輯器中編輯。
1. 在&#x200B;**輸出**&#x200B;標籤中，選取+圖示以建立DITA map的輸出預設集。

   ![](images/add-global-output-preset.png){width="350"}

1. 在&#x200B;**新增預設集**&#x200B;對話方塊中輸入下列詳細資料：
   - 類型
   - 名稱
   - Target \（適用於知識庫預設集\）
1. 選取&#x200B;**新增至資料夾設定檔**&#x200B;核取方塊以建立相關資料夾設定檔的輸出預設集，然後按一下&#x200B;**新增**。 預設集已建立，並顯示在所有相關地圖的&#x200B;**輸出**&#x200B;標籤下。 \( ![](images/global-preset-icon.svg)\)圖示表示資料夾設定檔層級預設集。
1. 輸入組態詳細資訊。 如需輸出預設集的詳細資訊，請檢視[瞭解輸出預設集](./generate-output-understand-presets.md)。

   >[!NOTE]
   >
   > 這些新增至資料夾描述檔的預設集與地圖無關，因此這些預設集的地圖特定設定不存在。

1. 您可以選取頂端的&#x200B;**產生預設集**&#x200B;圖示，以產生與已建立輸出預設集相關的地圖輸出。 您將會看到輸出產生程式的狀態。 若要檢視輸出，請將滑鼠指標停留在主題上，然後按一下&#x200B;**檢視輸出**。

>[!NOTE]
>
> AEM Guides也提供現成的PDF輸出預設集，用於產生DITA map的輸出。

**選項功能表的其他作業**

您也可以從「選項」選單對預設集執行下列操作：

- 選取預設集作為預設pdf預設集。 接著會使用選取的預設集作為預設預設集，以使用地圖的&#x200B;**下載為PDF**&#x200B;選項產生PDF輸出。
- 從&#x200B;**選項**&#x200B;功能表&#x200B;**編輯**、**重新命名**、**複製**&#x200B;或&#x200B;**刪除**&#x200B;現有的輸出預設集。

>[!NOTE]
>
> 刪除全域和資料夾設定檔中的輸出預設集時，該預設集將反映在所有相關對應中，且不會顯示在&#x200B;**輸出**&#x200B;標籤下。

**上層主題：**&#x200B;[&#x200B;使用網頁編輯器](web-editor.md)
