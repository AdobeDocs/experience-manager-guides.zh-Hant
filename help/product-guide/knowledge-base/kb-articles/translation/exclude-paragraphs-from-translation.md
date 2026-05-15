---
title: 從翻譯中排除主題中的段落
description: 如何從翻譯中排除主題中的段落
feature: Translation
role: User
exl-id: 21e41bb4-52f3-4352-92d9-4a60f636de99
TQID: https://experienceleague.adobe.com/IAY5PLpWlHEpMygjmHI-BqS75-VqAU5x1o9mdiu4Aac
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 148
ht-degree: 0%

---

# 如何從翻譯中排除主題中的段落

最簡單的方式是使用translation=no屬性。

+ 作者可以在不想翻譯的段落上插入額外的屬性，如&#x200B;**translation=no**。 需要通知翻譯廠商，他們可以在終端進行設定，以忽略具有此屬性的文字。
+ OOTB機器翻譯（搭配試用Microsoft翻譯聯結器）具有相同的行為。
+ 使用Microsoft翻譯進行測試：如果您在段落層級定義&#x200B;**translate=no**&#x200B;屬性，則不會翻譯完整的段落。 此屬性可在任何元素處定義，不會轉譯該元素內的內容。


以下是幾個熒幕擷取畫面，進一步說明此問題：

**Source內容**

![Source內容](assets/source-content.jpg)

**翻譯成西班牙文的內容**

![翻譯成西班牙文的內容](assets/trans-content.jpg)
