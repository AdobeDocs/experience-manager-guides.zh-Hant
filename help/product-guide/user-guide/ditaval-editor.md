---
title: 使用DITAVAL編輯器
description: 瞭解如何使用Adobe Experience Manager Guides中的DIVATAL Editor建立和編輯DITAVAL檔案。 瞭解DITAVAL編輯器如何在製作和來源檢視中支援DITAVAL檔案。
exl-id: f3901a4f-1925-42aa-b773-0d6f18175ce8
feature: Authoring, DITAVAL Editor
role: User
source-git-commit: 558cc1a724a483353eb5d912354e1ab37dab348a
workflow-type: tm+mt
source-wordcount: '1039'
ht-degree: 0%

---

# DITAVAL編輯器 {#ditaval-editor}

DITAVAL檔案用於產生條件輸出。 在單一主題中，您可以使用元素屬性來新增條件，以條件化內容。 然後，您會建立DITAVAL檔案，在其中指定應擷取以產生內容的條件，以及應從最終輸出中排除哪些條件。

Adobe Experience Manager Guides可讓您使用DITAVAL編輯器輕鬆建立及編輯DITAVAL檔案。 DITAVAL編輯器會擷取您系統中定義的屬性\（或標籤\），您可以使用它們來建立或編輯DITAVAL檔案。 如需有關在Adobe Experience Manager中建立和管理標籤的詳細資訊，請檢視Adobe Experience Manager檔案中的[管理標籤](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/tags.html?lang=en)區段。

以下各節涵蓋Experience Manager Guides中DITAVAL檔案可用的選項。

- [建立DITAVAL檔案](#create-ditaval-file)
- [編輯DITAVAL檔案](#edit-ditaval-file)
- [DITAVAl檔案編輯器檢視](#ditaval-editor-views)
- [在Assets UI中使用DITAVAL檔案](#working-with-ditaval-files-in-the-assets-ui)

## 建立DITAVAL檔案

執行以下步驟來建立DITAVAL檔案：

1. 在「存放庫」面板中，選取&#x200B;**新檔案**&#x200B;圖示，然後從下拉式功能表中選取&#x200B;**主題**。

   ![](images/new-file-option.png){width="800" align="left"}

   您也可以從[Experience Manager Guides首頁](./intro-home-page.md)以及存放庫檢視中資料夾的選項功能表存取此選項。

2. 顯示&#x200B;**新主題**&#x200B;對話方塊。

3. 在&#x200B;**新主題**&#x200B;對話方塊中，提供下列詳細資料：
   - 主題的標題。
   - \(Optional\)*主題的檔案名稱。 會根據主題「標題」自動建議檔案名稱。 如果您的管理員已根據UUID設定啟用自動檔案名稱，則您將不會檢視「名稱」欄位。
   - 主題將依據的範本。 若為DITAVAL檔案，請從下拉式清單中選取&#x200B;**Ditaval**。
   - 您要儲存主題檔案的路徑。 依預設，存放庫中目前所選資料夾的路徑會顯示在「路徑」欄位中。

   ![](images/new-topic-dialog-ditaval.png){width="300" align="left"}


4. 選取「**建立**」。

主題是在指定的路徑中建立。 此外，主題也會在編輯器中開啟以進行編輯。

![](images/ditaval-file-editor.png){width="800" align="left"}

## 編輯DITAVAL檔案

當您建立DITAVAL主題時，它會在編輯器中開啟以進行編輯。 若要編輯現有的DITAVAL主題，請導覽至DITAVAL主題所在的資料夾或地圖，然後從&#x200B;**選項**&#x200B;功能表選取&#x200B;**編輯**。

DITAVAL編輯器可讓您執行下列工作：

- 切換左側面板

  切換左側面板檢視。 如果您已透過DITA map開啟DITAVAL檔案，則地圖和存放庫會顯示在此面板中。 如需透過DITA map開啟檔案的詳細資訊，請檢視[透過DITA map編輯主題](map-editor-advanced-map-editor.md#id17ACJ0F0FHS)。

- 儲存

  儲存您在檔案中所做的變更。 所有變更都會儲存在檔案的目前版本中。

- 新增屬性

  在您的DITAVAL檔案中新增單一屬性。

  ![](images/ditaval-editor-props-new.png)

  第一個下拉式清單列出可在DITAVAL檔案中使用的允許DITA屬性。 有五個支援的屬性 — `audience`、`platform`、`product`、`props`和`otherprops`。

  第二個下拉式清單會顯示為選取的屬性設定的值。 然後，下一個下拉式清單會顯示您可在選取的屬性上設定的動作。 動作下拉式清單中允許的值為 — `include`、`exclude`、`passthrough`和`flag`。 如需這些值的詳細資訊，請檢視OASIS DITA檔案中[prop](http://docs.oasis-open.org/dita/dita/v1.3/errata01/os/complete/part3-all-inclusive/langRef/ditaval/ditaval-prop.html#ditaval-prop)元素的定義

- 新增所有屬性

  如果您要按一下即可新增系統中定義的所有條件屬性或屬性，請使用「新增所有屬性」功能。

  >[!NOTE]
  >
  > 如果DITAVAL檔案中已存在所有已定義的條件屬性，則無法新增更多屬性。 在此案例中，您會收到一則錯誤訊息。

  ![](images/ditaval-all-props-new.png)

完成編輯DITAVAL檔案後，請選取&#x200B;**儲存**。

>[!NOTE]
>
> 如果您關閉檔案而不儲存，變更將會遺失。 如果您不想將變更提交至Adobe Experience Manager存放庫，請選取&#x200B;**關閉**，然後在&#x200B;**未儲存的變更**&#x200B;對話方塊中選取&#x200B;**關閉而不儲存**。

## DITAVAL編輯器檢視

Adobe Experience Manager Guides的DITAVAL編輯器支援以兩種不同的模式或檢視檢視DITAVAL檔案：

**作者**：   這是DITAVAL編輯器的典型「所見即所得」檢視。 您可以使用簡單使用者介面新增或移除屬性，該介面會在下拉式清單中顯示屬性、屬性和動作。 在「作者」檢視中，您有選項可按一下插入個別屬性，以及插入所有屬性。

您也可以將指標暫留在檔案名稱上，找到目前使用的DITAVAL檔案版本。

**Source**：   Source檢視會顯示構成DITAVAL檔案的基礎XML。 除了在此檢視中進行一般文字編輯外，作者也可以使用「智慧型目錄」新增或編輯屬性。

若要叫用智慧型錄，請將游標放在任何屬性定義的結尾並輸入&quot;&lt;&quot;。 編輯器將顯示您可以在該位置插入的所有有效XML元素清單。

![](images/ditaval-source-view-new.png)


## 在Assets UI中使用DITAVAL檔案

您也可以從Assets UI建立DITAVAL檔案。 建立新DITAVAL主題的步驟如下：

1. 在Assets UI中，導覽至您要建立DITAVAL檔案的位置。

1. 選取&#x200B;**建立** \> **DITA主題**。

1. 在Blueprint頁面上，選取DITAVAL檔案範本，然後選取&#x200B;**下一步**。

1. 在[內容]頁面上，指定DITAVAL檔案的&#x200B;**標題**&#x200B;和&#x200B;**名稱**。

   >[!NOTE]
   >
   > 系統會根據檔案的標題自動建議名稱。 如果您要手動指定檔案名稱，請確定「名稱」不含任何空格、單引號或大括弧，且結尾為.ditaval。

1. 選取「**建立**」。

   「主題已建立」訊息便會顯示。

您可以選擇開啟DITAVAL檔案以在DITAVAL編輯器中編輯，或將主題檔案儲存在Adobe Experience Manager存放庫中。

執行以下步驟來編輯現有的DITAVAL檔案：

1. 在Assets UI中，導覽至您要編輯的DITAVAL檔案。

1. 若要取得檔案的獨佔鎖定，請選取該檔案，然後選取&#x200B;**簽出**。

1. 選取檔案並選取&#x200B;**編輯**，以在Adobe Experience Manager Guides DITAVAL編輯器中開啟檔案。



