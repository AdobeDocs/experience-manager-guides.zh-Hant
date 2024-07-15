---
sidebar_position: 8
source-git-commit: eb3fe92d36bc58a11e47f786a10d5938e2ed0184
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# 範例

在此套件中，我們也提供了一些自訂範例（可在`guides_extension/src`取得） 。 以下為各範本的簡短說明。

1. [內容功能表](./../../src/file_options.ts)
在此範例中，我們已自訂`file_options`內容功能表，以移除`Delete`和`Edit`選項，並將`Duplicate`選項取代為`Download`選項。

2. [左側面板](../../src/left_panel_container.ts)
在此範例中，我們已自訂`left tab panel`，讓另一個`tab`名為「TEST EXTENSION」，以及對應的`tab panel`有標籤： `Test Tab Panel`

3. [右側面板](../../src/right_panel_container.ts)
在此範例中，我們已自訂`right tab panel`，讓另一個`tab`名為「TEST EXTENSION」，以及對應的`tab panel`有標籤： `New Tab Panel`

4. [存放庫面板](../../src/repository_panel.ts)

5. [工具列](../../src/toolbar.ts)
在此範例中，我們已將`Insert Element`、`Insert Paragraph`、`Insert Numbered List`、`Insert Bulleted List`按鈕取代為包含所有這些按鈕的單一`More Insert Options`按鈕。

[檢閱應用程式範例]

1. [註解工具箱](../../src/review_app_examples/annotation_extension.ts)
在此範例中，我們已將另一個按鈕新增到註釋工具箱，以在AEM中開啟目前的稽核主題。

2. [檢閱評論](../../src/review_app_examples/review_comment.ts)
在此範例中，我們已新增以使用者資訊（包含評論者的全名和標題）取代使用者名稱、新增唯一評論ID、mailTo圖示，以及新增用於提及評論嚴重性和理由的輸入欄位。
我們也在開啟對話方塊的XMLEditor側之註解上新增了`accept with modification`按鈕。

3. [註解回覆](../../src/review_app_examples/comment_reply.ts)
在此範例中，我們已新增以使用者資訊取代使用者名稱（包含評論者的完整名稱和標題），並在評論標題中新增mailTo圖示。

4. [內嵌稽核面板](../../src/review_app_examples/inline_review_panel.ts)
在此檔案中，我們會計算並指派在`Review Comment`和`Comment Reply`範例中提及的唯一註解ID。
   - `setCommentId`方法會根據註解計數，為每個註解設定唯一的註解ID。

   - `setUserInfo`會使用每個註解的完整名稱和標題來設定userInfo的值。

   - `onNewCommentEvent`會確保為每個新註解或回覆呼叫`setUserInfo`方法。

   - `updatedProcessComments`函式會針對每個新註解事件執行，並確保在收到新註解事件時呼叫`setCommentId`。

5. [主題評論面板](../../src/review_app_examples/topic_reviews.ts)：此檔案會擴充[內嵌評論面板](../../src/review_app_examples/inline_review_panel.ts)，讓新增的自訂功能也可在評論應用程式端運作。

6. [接受修改對話方塊](../../src/review_app_examples/accept_with_modification_dialog.ts)
這是將新Widget新增至應用程式的範例。 我們已在此建立新的對話方塊，其中包含兩個輸入文字欄位： `Revised Text`和`Adjudicator Comment Rationale`

![接受修改對話方塊](./imgs/accept_with_modification_dialogue.png)

以下是自訂前後的檢閱面板：

![檢閱面板；](./imgs/review_panel.png)
![接受並修改對話方塊](./imgs/customised_review_panel.png)
