---
title: 設定SCORM預覽的內容安全性原則
description: 瞭解如何使用Cloud Manager中的環境變數設定SCORM預覽的內容安全性原則
feature: Authoring
role: User
source-git-commit: 730fe6021aa20aa2b57801807da0f471f84a7718
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---


# 設定SCORM預覽的內容安全性原則(CSP)

Experience Manager Guides SCORM預覽可透過專用環境變數來管理，該變數會管理套用至預覽體驗的內容安全性原則(CSP)。 啟用此設定後，管理員可以新增其他信任的來源來擴充此設定。 這些來源可能包括SCORM套件在Experience Manager Guides中正確載入和轉譯預覽所需的指令碼、樣式、字型、影像、媒體、框架及其他專案。

本文說明如何在Cloud Manager中新增及設定環境變數，並劃分JSON值中每個欄位的功能，以及說明如何在需求變更時稍後更新值。

## 設定欄位

變數`GUIDES_SCORM_PREVIEW_CONFIG`接受JSON物件作為其值。 每個值都會控制在SCORM預覽期間套用的CSP的特定層面：

| 欄位 | 類型 | 說明 |
|---|---|---|
| `CSP_ENABLED` | 布林值 | 針對SCORM預覽開啟(`true`)或關閉(`false`) CSP強制執行。 |
| `ALLOW_UNSAFE_EVAL` | 布林值 | 當設定為`true`時，允許使用`eval()`和類似的不安全JavaScript評估方法。 |
| `ADDITIONAL_SCRIPT_SRC` | 陣列 | 允許提供JavaScript的其他受信任來源。 |
| `ADDITIONAL_STYLE_SRC` | 陣列 | 允許提供樣式表的其他受信任來源。 |
| `ADDITIONAL_FONT_SRC` | 陣列 | 允許提供字型的其他受信任來源。 |
| `ADDITIONAL_FRAME_SRC` | 陣列 | 允許在`<iframe>`元素中載入其他信任的來源。 |
| `ADDITIONAL_IMG_SRC` | 陣列 | 允許提供影像的其他受信任來源。 |
| `ADDITIONAL_MEDIA_SRC` | 陣列 | 允許提供音訊/視訊內容的其他信任來源。 |
| `ADDITIONAL_WORKER_SRC` | 陣列 | 允許為Web工作者提供服務的其他受信任來源。 |
| `ADDITIONAL_CONNECT_SRC` | 陣列 | 允許預覽連線到的其他受信任來源（例如XHR/擷取呼叫）。 |
| `ADDITIONAL_MANIFEST_SRC` | 陣列 | 允許提供Web應用程式資訊清單的其他受信任來源。 |
| `ADDITIONAL_OBJECT_SRC` | 陣列 | 允許透過`<object>`、`<embed>`或`<applet>`載入其他信任的來源。 |


## 設定欄位的預設值

```json
{
  "CSP_ENABLED": true,
  "ALLOW_UNSAFE_EVAL": false,
  "ADDITIONAL_STYLE_SRC": ["https://fonts.googleapis.com"],
  "ADDITIONAL_FONT_SRC": ["https://fonts.gstatic.com"],
  "ADDITIONAL_FRAME_SRC": ["https://www.youtube-nocookie.com", "https://www.youtube.com"],
  "ADDITIONAL_SCRIPT_SRC": [],
  "ADDITIONAL_WORKER_SRC": [],
  "ADDITIONAL_IMG_SRC": [],
  "ADDITIONAL_MEDIA_SRC": [],
  "ADDITIONAL_CONNECT_SRC": [],
  "ADDITIONAL_MANIFEST_SRC": [],
  "ADDITIONAL_OBJECT_SRC": []
}
```

根據您的需求，您不需要填入每個值；如果您不需要允許其他來源，請將任何來源型別保留為空白陣列。

>[!NOTE]
>
> 若要停用SCORM預覽的CSP強制執行，請在JSON值中設定`"CSP_ENABLED": false`。

## 在Cloud Manager中新增變數

1. 登入Cloud Manager並選取您要套用設定的環境。
2. 導覽至環境的&#x200B;**組態**&#x200B;標籤。
3. 選取&#x200B;**新增/更新**&#x200B;以新增環境變數。

   ![正在新增變數至Cloud Manager ](assets/add-new-variable.png){width="650"}

4. 在&#x200B;**名稱**&#x200B;欄位中輸入變數(`GUIDES_SCORM_PREVIEW_CONFIG`)的名稱。

   ![在名稱欄位中新增變數的名稱](assets/variable-name.png){width="650"}

5. 在&#x200B;**值**&#x200B;欄位中輸入完整的JSON設定，包括課程需求的來源允許清單。
6. 選取&#x200B;**套用的服務**，以選擇變數應套用至&#x200B;**作者**、**發佈**，或兩者皆套用。 若為Experience Manager Guides製作，請選取&#x200B;**作者**。
7. 在&#x200B;**型別**&#x200B;欄位中選取&#x200B;**變數**。
8. 選取「**新增**」。
9. 選取「**儲存**」。

   ![儲存要套用至環境的變數](assets/save.png){width="650"}

儲存後，Cloud Manager會將設定套用至選取的環境。 這通常需要10到12分鐘的時間來傳播，因此請預留時間讓更新完成。 完成後，新設定將在該環境中啟用SCORM預覽。

## 更新變數值

如果您的需求變更，您可以隨時從Cloud Manager中的相同Configuration索引標籤重新造訪`GUIDES_SCORM_PREVIEW_CONFIG`變數。 找出現有的變數，並選取其&#x200B;**新增/更新**&#x200B;選項以開啟變數進行編輯，然後視需要修訂值。