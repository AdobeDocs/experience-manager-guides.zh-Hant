---
title: 根據自訂範本建立地圖
description: 瞭解如何建立自訂範本、使用範本建立新的地圖檔案，並將定義的標題傳遞給AEM Guides中的DITA map。
feature: Authoring, Map Editor
role: User
source-git-commit: 76c731c6a0e496b5b1237b9b9fb84adda8fa8a92
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 0%

---

# 根據自訂範本建立地圖 {#id225VF0808MP}

您可以建立自訂對映範本，並使用它們來建立DITA對映，以及主題範本和對映範本中參照的對映範本

您可以參照自訂對應範本中的其他對應範本和主題範本。 參照的對映範本可參照各種對映範本、主題範本、主題、對映、影像、影片和其他資產。 自訂的對映範本可以幫助您輕鬆複製對映範本和整個參照的資料夾結構。 這些自訂範本對於建立和重新建立具有遞回結構和參照的多個對映特別有用。

>[!NOTE]
>
> 主題範本不會以遞回方式建立。 系統只會產生直接位於對映範本內的主題範本，而主題範本內的任何主題範本只會直接在父項中參照。

## 建立自訂範本

AEM Guides可讓您從dita-templates資料夾建立自訂地圖和主題。 您可以使用這些自訂範本來建立地圖和主題。 您也可以將這些範本與作者共用，讓作者使用範本建立檔案。 使用這些範本，您可以讓作者保留範本資料夾中特定資源的個別副本。

>[!NOTE]
>
> 所有僅可在其中參照和維護的資源都必須放在範本資料夾之外。


您可以透過下列方式建立地圖和主題範本：
1. [左側面板](./web-editor-features.md#left-panel-id2051ea0m0hs)的範本窗格
1. [Assets UI中的範本](#templates-assets-ui)
1. [選項功能表](#templates-in-assets-ui)

### Assets UI中的範本 {#templates-assets-ui}

**主題範本**

執行以下步驟來建立主題範本：

1. 在&#x200B;**Assets UI**&#x200B;中，導覽至dita-templates資料夾。

   ![](images/dita-templates.png){width="800" align="left"}

1. 按一下&#x200B;**主題**&#x200B;資料夾以開啟它。按一下&#x200B;**建立\> DITA範本**。
1. 在Blueprint頁面上，選取&#x200B;**主題**，然後按一下&#x200B;**下一步。**
1. 在[內容]頁面上，指定主題範本&#x200B;**標題**。
1. 指定檔案&#x200B;**名稱**

   >[!NOTE]
   >
   > 檔案名稱必須具有.dita副檔名。

1. \(Optional\)新增說明。
1. 按一下「**建立**」。主題範本建立的訊息隨即顯示。 然後，您可以開啟主題範本並進行編輯。

**對應範本**

執行以下步驟來建立對映範本：

1. 在&#x200B;**Assets UI**&#x200B;中，導覽至dita-templates資料夾。
1. 按一下&#x200B;**對應**&#x200B;資料夾以開啟。
1. 按一下&#x200B;**建立\> DITA範本。**

   ![](images/create-dita-template.png){width="300" align="left"}

1. 在Blueprint頁面上，選取&#x200B;**地圖**&#x200B;並按一下&#x200B;**下一步**。
1. 在[內容]頁面上，指定對應範本&#x200B;**Title**。
1. 指定檔案&#x200B;**名稱**。

   >[!NOTE]
   >
   > 檔案名稱必須具有.ditamap副檔名。

1. （選擇性\）新增說明。按一下&#x200B;**建立**。 對應範本建立的訊息隨即出現。 然後，您可以開啟對映範本並進行編輯。 您可以在對應範本中新增主題範本、對應範本以及其他資產的參考。

### 選項功能表 {#options-menu}

若要建立地圖或主題範本，請執行下列步驟：

1. 選取目前範本資料夾中的&#x200B;**Map**&#x200B;或&#x200B;**Topic**&#x200B;資料夾。 例如，`dita-templates` 資料夾。
1. 從&#x200B;**選項**&#x200B;功能表，選取&#x200B;**建立地圖範本**&#x200B;或&#x200B;**建立主題範本**。

   **建立新地圖範本**&#x200B;或&#x200B;**建立新主題範本**&#x200B;對話方塊開啟。
1. 輸入新範本的標題和名稱。
1. 從&#x200B;**範本**&#x200B;下拉式清單中選擇要建立的範本型別。

對應範本建立的訊息隨即出現。 您可以將範本新增至全域或資料夾層級的設定檔。 然後，新範本會出現在主題或地圖建立程式中，您可以使用它來建立地圖或主題。


您的管理員也可以建立資料夾，並將其設定為您可建立和儲存範本的資料夾。

根據您的設定，瞭解如何設定自訂DITA範本資料夾路徑：

+++ 雲端服務

瞭解如何在Cloud Service安裝與設定指南中[設定自訂DITA範本資料夾路徑](/help/product-guide/install-guide/conf-template-tags-custom-dita-topic-template.md#configure-custom-dita-template-folder-path-id191lcf0095z){target="_blank"}。

+++

+++ 內部部署軟體

瞭解如何在On-premise Installation and Configuration Guide中[設定自訂DITA範本資料夾路徑](/help/product-guide/cs-install-guide/conf-template-tags-custom-dita-topic-template.md#configure-custom-dita-template-folder-path-id191lcf0095z)。

+++

## 傳遞範本中定義的標題

如果您想要將範本內使用的主題或地圖示題傳遞給使用該範本建立的DITA map，請在標題周圍使用大括弧。

範例

```XML
<pubtitle>
   <mainpubtitle outputclass="booktitle">
   {title}
   </mainpubtitle>
   <subtitle>Subtitle</subtitle>
</pubtitle>

The resultant DITA map with title "Rootmap1" will look like as follows:
<pubtitle>
   <mainpubtitle outputclass="booktitle">Rootmap1
   </mainpubtitle>
   <subtitle>Subtitle</subtitle>
</pubtitle>
```

>[!NOTE]
> 只有第一個出現的花括弧會取代為標題。

如果您未在標題周圍使用大括弧，則只會挑選第一個元素，且不會從範本中挑選標題的巢狀，如下所示：

```XML
<pubtitle> Rootmap1 </pubtitle>
```

>[!NOTE]
> 您也可以使用文字周圍的大括弧，將其巢狀結構從自訂範本傳遞至DITA map。

範例

```XML
<title>    
    <sub>        
        <b>{title}</b>    
    </sub>
</title>
```




## 使用地圖範本建立新地圖

>[!NOTE]
>
> 對應範本必須設定好並由您的管理員提供撰寫功能。 如需詳細資訊，請參閱安裝和設定Adobe Experience Manager Guidesas a Cloud Service中的&#x200B;*設定撰寫範本*&#x200B;區段。

執行以下步驟，使用自訂地圖範本建立地圖：

1. 在&#x200B;**Assets UI中，**&#x200B;導覽至您要建立對應的資料夾。
1. 按一下&#x200B;**建立\> DITA Map**。
1. 在Blueprint頁面上，選取您要使用的對應範本，然後按一下[下一步]。**** 例如，如果您已建立對應範本&#39;test-template&#39;，請選取它。
1. 在[屬性]頁面上，指定對應&#x200B;**標題**。
1. 指定檔案&#x200B;**名稱**。

   >[!NOTE]
   >
   > 檔案名稱必須具有.ditamap副檔名。

1. 按一下「**建立**」。對應建立的訊息就會出現。


對應會產生在範本資料夾內參照的所有資產。 地圖中引用的某些資產型別可能如下所示：

- 如果對應包含主題範本的參照，則會在該資料夾中建立一個副本，其階層與`dita-templates`資料夾中主題資料夾的階層相同。
- 如果對應包含對對應範本的參照，則會在該資料夾中建立其副本，其階層與`dita-templates`資料夾中的對應資料夾相同。
- 如果對應包含`dita-templates/topics`或`dita-templates/maps`資料夾外部之主題或對應的泛型參考，則只會參考該主題或對應，而不會建立副本。

  >[!NOTE]
  >
  > `dita-templates/topics`和`dita-templates/maps`是參考線中的預設路徑，且可設定。


  如果對應範本中有主題範本索引鍵定義，則會建立新索引鍵\（因此為新主題\），並在對應中參照。

- 如果在資料夾的相同層級建立另一個地圖或主題，則新建立的資產名稱會附加0、1、2等等。 您可以選擇開啟地圖進行編輯，或將地圖檔案儲存在存放庫中。

**父級主題：**[&#x200B;使用對應編輯器](map-editor.md)
