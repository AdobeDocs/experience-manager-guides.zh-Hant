---
title: 檢視輸出產生工作的狀態
description: 檢視FrameMaker檔案的輸出產生佇列。 瞭解如何檢視輸出產生任務的狀態。
feature: Publishing FrameMaker Documents
role: User
hide: true
exl-id: bf5a4365-0183-43d5-a39a-b9eb8a34b27d
TQID: https://experienceleague.adobe.com/FP5RxNtyWcdS-xpw2Atttt3x6DHx73Ljv-Ym91IxY5s
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: d90290ec-3e61-4ebd-8649-bcafe0836803
subfeature_v2:
  - id: bf79f6d3-0ad0-4d82-99e4-42ce98324d60
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 7ba2ad081f90fcbd38c7b34524a9ed1378e64f0d
workflow-type: tm+mt
source-wordcount: 544
ht-degree: 0%

---

# 檢視輸出產生工作的狀態 {#viewing_output_history}

當您啟動FrameMaker檔案的輸出產生任務後，AEM Guides會將此任務傳送至輸出產生佇列。 此佇列會即時更新，顯示佇列中每個輸出產生工作的狀態。

執行以下步驟來檢視輸出產生佇列：

1. 在Assets UI中，導覽至並按一下您要檢查輸出產生狀態的FrameMaker檔案。

1. 按一下「輸出」。

   ![](images/output-queued-fm.png){width="800"}

1. 「輸出」頁面分為兩個部分：

   - **佇列輸出：**

     列出等待產生或正在產生程式中的輸出。 您也可以找到用於已排入佇列之任務的輸出產生設定或預設集、型別、啟動任務的使用者、任務已排入佇列後的時間以及目前狀態。

   - **產生的輸出**

     列出已完成的輸出工作。 同樣地，此處顯示的資訊與「佇列輸出」區段類似，只是輸出產生時間有差異。

     在此清單中，您可能會有成功執行或失敗的工作。 對於已成功完成的工作，發佈程式會建立記錄檔\(logs.txt\)，按一下「產生時間」欄中的連結即可存取該記錄檔。

> **如何定義資料表的多個儲存格、整列或欄的屬性**
>
> 您可以在儲存格、列或欄層級定義屬性
>
> <details>
>&gt; <summary>顯示步驟</summary>
>
> 您也可以在表格的多個儲存格、整列或欄上定義屬性。 例如，若要對齊表格儲存格，請拖曳並選取所需的儲存格。 在「內容屬性」面板（右側）中，屬性&#x200B;**Type**&#x200B;變更為&#x200B;**entry**。
>
> 1. 在&#x200B;**屬性**&#x200B;區段中，選取&#x200B;**+新增**。
> 1. 從&#x200B;**屬性**&#x200B;下拉式清單中選取`@valign`屬性。
> 1. 從值下拉式清單中，選取您想要套用至所選表格儲存格的文字對齊方式。
> 1. 選取&#x200B;**新增。**
>
> ![](images/align-table-cell_cs.png)
>
> </details>



**定義資料表的多個儲存格、整列或欄的屬性**

您可以在儲存格、列或欄層級定義屬性。

<details>
<summary>顯示步驟</summary>

您也可以在表格的多個儲存格、整列或欄上定義屬性。 例如，若要對齊表格儲存格，請拖曳並選取所需的儲存格。 在「內容屬性」面板（右側）中，屬性&#x200B;**Type**&#x200B;變更為&#x200B;**entry**。

1. 在&#x200B;**屬性**&#x200B;區段中，選取&#x200B;**+新增**。
1. 從&#x200B;**屬性**&#x200B;下拉式清單中選取`@valign`屬性。
1. 從值下拉式清單中，選取您想要套用至所選表格儲存格的文字對齊方式。
1. 選取&#x200B;**新增。**

   ![](images/align-table-cell_cs.png)

   </details>

>[!BEGINSHADEBOX]
>
> **如何定義資料表的多個儲存格、整列或欄的屬性**
>
> 您可以在儲存格、列或欄層級定義屬性。
>
> <details>
>&gt; <summary>顯示步驟</summary>
>
> 您也可以在多個儲存格、整列或表格的一欄上定義屬性。 例如，若要對齊表格儲存格，請拖曳並選取所需的儲存格。 在「內容屬性」面板（右側）中，**Type**&#x200B;屬性變更為&#x200B;**entry**。
>
> 1. 在&#x200B;**屬性**&#x200B;區段中，選取&#x200B;**+新增**。
> 1. 從&#x200B;**屬性**&#x200B;下拉式清單中選取`@valign`屬性。
> 1. 從&#x200B;**值**&#x200B;下拉式清單中，選取所要的文字對齊方式。
> 1. 選取「**新增**」。
>
> ![](images/align-table-cell_cs.png)
>
> </details>
>
>[!ENDSHADEBOX]




**父級主題：**&#x200B;[&#x200B;產生FrameMaker檔案的輸出](fm-output-generatation.md)

