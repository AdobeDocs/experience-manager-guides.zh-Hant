---
title: 使用標籤
description: 探索Adobe Experience Manager Guides中不同版本檔案的標籤使用情形。 瞭解如何在主題版本中新增或刪除標籤。
exl-id: d116906d-b469-4a97-b0af-4fadbe15222b
feature: Authoring, Features of Web Editor, Publishing
role: User
TQID: https://experienceleague.adobe.com/sOFJReXzhdWNvsDCcM-s5c5gN-YzV7juLkbGWxbz4bw
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: d4f22c6d-7923-41e5-9da3-527ff8df4bc8id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 535
ht-degree: 0%

---

# 使用標籤 {#id164JBG0M0T1}

Adobe Experience Manager Guides可讓您將標籤新增至檔案的不同版本。 您可以使用這些標籤來指定要包含在基準線中以供發佈的版本。 如需使用標籤建立基準線的詳細資訊，請檢視[使用基準線](generate-output-use-baseline-for-publishing.md#)。

例如，如果您要在&#x200B;*版本2.0*&#x200B;中使用&#x200B;*版本1.0*&#x200B;中主題的&#x200B;*版本1.0*&#x200B;和&#x200B;*版本1.1*&#x200B;中的相同主題，您可以在&#x200B;*版本1.0*&#x200B;上新增&#x200B;*版本1.0*&#x200B;標籤，在&#x200B;*版本1.1*&#x200B;上新增&#x200B;*版本2.0*&#x200B;標籤。

新增標籤之後，您可以建立基準線，並指定使用該基準線發佈時應該包含的主題版本。 若要檢視基準線中應包含或排除的版本，您可以使用「版本記錄」選項。

## 從編輯器新增標籤

執行以下步驟，從編輯器將標籤新增至主題：

1. 在「存放庫」面板中，導覽至主題並在編輯器中開啟它。
1. 從&#x200B;**功能表**&#x200B;下拉式清單中選取&#x200B;**版本標籤**。

   顯示&#x200B;**版本標籤管理**&#x200B;對話方塊。

1. 在&#x200B;**版本標籤管理**&#x200B;對話方塊中，選取您要新增標籤的版本。
1. 選取選取版本的標籤，並選取&#x200B;**新增標籤**。

   ![](images/version-label-management-dialog-new.png){width="650"}

   >[!NOTE]
   >
   > 您無法將相同的標籤新增至主題的不同版本。 不過，您可以將多個標籤新增至主題的相同版本。
1. 確認以在確認提示中套用標籤。

   標籤會顯示在所選主題的「版本記錄」中。

   ![](images/label-comparison-version-history.png){width="650"}

   >[!NOTE]
   >
   > 您可以使用基準線將標籤新增至多個主題。 如需使用基準線新增標籤的詳細資訊，請檢視[新增標籤至基準線](generate-output-use-baseline-for-publishing.md#id184KD0T305Z)。

若要從主題中刪除版本標籤，請使用針對「版本標籤管理」對話方塊中新增的每個標籤提供的&#x200B;**移除**&#x200B;圖示。

![](images/remove-version-label.png)


## 從Assets UI使用標籤

您也可以新增標籤至主題，並視需要從Assets UI中刪除標籤。

執行以下步驟，從Assets UI將標籤新增至主題：

1. 在Assets UI中，選取主題並開啟它。
1. 選取左側邊欄選擇器圖示，然後選取&#x200B;**版本記錄**。
1. 在「版本記錄」下拉式清單中，選取您要新增標籤的版本。
1. 輸入所選版本的標籤，然後按Enter鍵。 例如，*2.6版本*。

   >[!NOTE]
   >
   > 您無法將相同的標籤新增至主題的不同版本。 不過，您可以將多個標籤新增至主題的相同版本。

   標籤會顯示在所選主題的「版本記錄」中。 下列熒幕擷圖顯示已新增至主題反白版本中的標籤&#x200B;*x.x版本*&#x200B;和&#x200B;*使用手冊*。

   ![](images/labels.png){width="300"}

>[!NOTE]
>
> 您可以使用基準線將標籤新增至多個主題。 如需使用基準線新增標籤的詳細資訊，請檢視[新增標籤至基準線](generate-output-use-baseline-for-publishing.md#id184KD0T305Z)。

若要從主題中刪除版本標籤，請使用「版本記錄」面板中針對每個標籤提供的&#x200B;**刪除**&#x200B;按鈕。

![](images/delete-labels.png){width="300"}


**父級主題：**[&#x200B;編輯器簡介](web-editor.md)
