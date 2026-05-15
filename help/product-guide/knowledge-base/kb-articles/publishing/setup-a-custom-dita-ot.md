---
title: 在 [!DNL AEM Guides]中設定自訂DITA-OT
description: 瞭解如何在 [!DNL Adobe Experience Manager Guides]中設定自訂DITA-OT
role: Admin
exl-id: f479c2cf-5b8b-4517-be97-81303468007a
feature: DITA-OT Configuration
TQID: https://experienceleague.adobe.com/EaU6rkZL-RBkkYDhKxHNkizIVSqNzEDd-TtFlJAmREw
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 174
ht-degree: 0%

---

# 在[!DNL AEM Guides]中為AEM設定自訂DITA-OT

新增自訂DITA-OT的步驟已記錄在&#x200B;_安裝與組態指南_&#x200B;的&#x200B;_使用自訂DITA-OT外掛程式_&#x200B;一節。

就高層級而言，步驟如下：

+ 取得基本DITA-OT
   + 如果您要從[!DNL AEM Guides]取得現成可用的DITA-OT復本，請從路徑`/etc/fmdita/dita_resources/DITA-OT.zip`下載
   + 如果您想要取得其他版本，可以從[dita-ot存放庫](https://www.dita-ot.org/download)下載
+ 對DITA-OT進行變更，例如[新增外掛程式](https://www.dita-ot.org/dev/topics/plugins-installing.html)，或自訂現有外掛程式（請參閱以下相關連結章節中的範例）
+ 上傳已接收的`DITA-OT.zip`至`/apps/<project-folder>/dita_resources` （建議使用建立自訂專案資料夾的方法）
+ 透過&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 指南]** > **[!UICONTROL DITA設定檔]**新增DITA設定檔（使用上傳自訂DITA-OT的DITA-OT路徑，請參閱下方的熒幕擷圖）
  ![個DITA設定檔](assets/dita-profile.png)

>[!MORELIKETHIS]
>
>+ [自訂DITA-OT外掛程式範例](https://www.dita-ot.org/dev/topics/pdf-customization.html)
