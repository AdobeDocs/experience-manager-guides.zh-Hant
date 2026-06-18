---
title: 使用條件式內容
description: 瞭解如何在 [!DNL AEM Guides]中建立條件，然後設定條件式內容產生
role: User
exl-id: a86007e3-48d1-458b-84a7-b683e113e5b2
feature: Publishing
TQID: https://experienceleague.adobe.com/3Gz6-sJn7dvzJSlnKgRoRqpFTqtj5fiVlAjOv0lbD1o
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: 262
ht-degree: 0%

---

# 使用條件式內容

**使用案例**

* 作者可以設定內容條件，以控制是否顯示在輸出中。

* 作者可在發佈時選擇顯示/隱藏不同的條件。

* 例如，作者可以在內容中新增屬性為1.0版和2.0版，並使用條件來包含1.0版的1.0版和排除2.0版。

**步驟1**

在[!UICONTROL 資料夾設定檔]中定義與檔案相關的條件：
請參閱《安裝與組態指南》第69頁[中的&#x200B;**設定全域或資料夾層級設定檔的條件屬性**&#x200B;一節](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf)

![在資料夾設定檔中設定條件](assets/conditions-in-profiles.png)

**步驟2**

在XML編輯器中選取&#x200B;**使用者偏好設定**&#x200B;中步驟1定義的&#x200B;**[!UICONTROL 資料夾設定檔]**：
請參閱使用手冊[&#128279;](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_User-Guide_EN.pdf)第41頁中的&#x200B;**使用者偏好設定**&#x200B;節


**步驟3**

使用條件來條件化內容的區段：
請參閱使用手冊[&#128279;](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_User-Guide_EN.pdf)第90頁中的&#x200B;**條件**&#x200B;小節

![在編輯器中使用條件](assets/conditions-in-web-editor.png)

**步驟4**

定義對應層級的條件預設集，以選擇要於輸出中啟用的條件：
請參閱使用手冊[&#128279;](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_User-Guide_EN.pdf)第249頁中的&#x200B;**使用條件預設集**&#x200B;節
