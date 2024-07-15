---
title: 在 [!DNL AEM Guides]中設定自訂DITA-OT
description: 瞭解如何在 [!DNL Adobe Experience Manager Guides]中設定自訂DITA-OT
role: Admin
exl-id: f479c2cf-5b8b-4517-be97-81303468007a
feature: DITA-OT Configuration
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '143'
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
