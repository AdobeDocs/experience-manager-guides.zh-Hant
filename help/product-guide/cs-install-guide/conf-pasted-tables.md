---
title: 自訂Web編輯器
description: 瞭解如何在編輯器中自訂貼上表格的顯示
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 839128b4-4889-4c61-b1c0-214ba1d3165e
TQID: https://experienceleague.adobe.com/0g3LyLfKxZEbtl968wJK6r1xPHRjagayeBF4xSvJF6c
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
  - id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 223
ht-degree: 0%

---

# 設定已貼上表格的顯示

使用編輯器中的次要工具列，您可以在主題的目前或下一個有效位置插入簡單表格。 您也可以從Microsoft Word或Excel複製表格，然後直接將表格貼到主題檔案中。

管理員可以設定複製表格的顯示方式。 依預設，此類複製的表格在編輯器中會顯示為`simpletable`。 不過，您可以更新XML編輯器組態設定，將此設定變更為將複製的表格顯示為`tgroup`。

>[!NOTE]
>
> 如果您複製含有合併列或欄的表格，則該表格將會貼上為一般表格`trgoup`，而非`simpletable`，無論XML編輯器設定中設定的表格設定為何。

若要更新預設表格格式，請執行下列步驟：

1. 開啟「Adobe Experience Manager導覽」頁面，然後選取左側的&#x200B;**工具**。
2. 在「工具」面板中，從工具清單中選取&#x200B;**參考線**。
3. 選取&#x200B;**資料夾設定檔**，然後選取您要更新表格設定的設定檔。
4. 瀏覽至&#x200B;**XML編輯器組態**&#x200B;標籤。
5. 選取頂端的&#x200B;**編輯**&#x200B;圖示。
6. 選取「**下載**」圖示以在本機系統上下載`ui_config.json`檔案。
7. 在`ui_config.json`檔案中，更新`simpletable`設定，如下所示：

   ```
   "htmlToDitaMapping":{ "table": {
   "name" : "tgroup",
   "wrapTag" : {
       "dita" : "table",
       "html" : "div"
   }
   } },
   ```


更新後，儲存檔案並上傳它。
