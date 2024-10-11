---
title: 發行說明 | Adobe Experience Manager Guides 2024.10.0版的新增功能
description: 瞭解2024.10.0版Adobe Experience Manager Guides中的新功能和增強功能
role: Leader
source-git-commit: 545e51cbd970aa3df01a0fe2461a2e730c0db66a
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 1%

---

# 2024.10.0版（2024年10月）的新增功能

本文介紹2024.10.0版Adobe Experience Manager Guides as a Cloud Service所推出的新功能和增強功能。

有關此版本中的問題修正清單，請查看 [2024.10.0 版本中修正的問題](fixed-issues-2024-10-0.md)。

瞭解2024.10.0 ](../release-info/upgrade-instructions-2024-10-0.md)版的[升級指示。


## 發佈增強功能

2024.10.0版本已進行下列內容發佈增強功能：




### 內容片段發佈中的增強功能

Experience Manager Guides也在內容片段中提供一些實用的增強功能：

- Experience Manager Guides可讓您將主題或其元素發佈至內容片段。

- 您可以從&#x200B;**檔案屬性**&#x200B;中的&#x200B;**輸出**&#x200B;區段，發佈並檢視主題的內容片段。


- 您可以在發佈至內容片段時，透過篩選包含條件的內容來輕鬆建立內容片段變體。

- 使用新的對應介面來輕鬆選取元素並發佈至內容片段。

現在，內容片段發佈只會取代對應的內容，而不會覆寫完整的內容片段。 此功能允許內容片段包含來自多個來源的資料，例如多個主題或內容片段編輯器。

![在Publish中新增片段模型和對應詳細資訊作為內容片段對話方塊](assets/content-fragment-mapping.png)

如需詳細資訊，請檢視[Publish內容片段](../user-guide/publish-content-fragment.md)。


### 根據條件篩選器的Publish體驗片段變體

Experience Manager Guides可讓您將主題或其元素發佈至體驗片段。 現在，您也可以使用條件或DITAVAL篩選器來建立體驗片段變體，並跨不同管道或針對不同對象重複使用。

進一步瞭解如何[Publish體驗片段](../user-guide/publish-experience-fragment.md)。


### 重新組織AEM Sites預設集以方便使用

設定已重新整理，以幫助您快速設定輸出預設集並產生AEM Sites輸出。
您可以在**新的輸出預設集**&#x200B;對話方塊中選取&#x200B;**使用舊版元件對應**&#x200B;選項，以建立現有的AEM Sites預設集。

檢視AEM Sites預設集中的&#x200B;**一般**、**內容**&#x200B;和&#x200B;**交叉對應參考**&#x200B;標籤：
- **一般**：包含產生輸出的一般組態。 您可以指定網站和輸出路徑、刪除或覆寫現有的輸出頁面、刪除先前為移除的主題產生的頁面、選取設計範本、保留暫存檔案，以及指定產生後的工作流程。
- **內容**：包含適用於輸出產生內容的設定。 您可以選取篩選器、DITA map的基準線，以及發佈的中繼資料屬性。
- **交叉對應參考**：此清單包含的主題包含範圍=&quot;peer&quot;的交叉對應參考。 您可以為其他DITA map中可用主題的scope=&quot;peer&quot;交叉對映參照清單指定發佈內容。 如果您使用Experience Manager Guides (UUID)版本，此標籤就會出現。



### 來自網頁編輯器中AEM Sites預設集的交叉對應參考

Experience Manager Guides的最新增強功能在網頁編輯器的AEM Sites預設集中引入了跨對應參照。
Experience Manager Guides中的跨地圖參照有助於改善內容導覽、增加內容重複使用率並增強使用者體驗。


您可以指定發佈前後關聯，以取得其他具有scope=&quot;peer&quot;的DITA map中可用主題的交叉對映參照清單。 例如，地圖A中的主題1包含對主題2的參照。 主題2可以出現在單一或多個地圖中。  您可以選取上層地圖和特定的預設集，或每個連結最近發佈的輸出。

如果同一主題在檔案中被參照多次，則您可以為每個執行個體新增不同的發佈內容。 這可提供更大的彈性並控制其內容。 例如，主題3同時存在於對映B和對映C中。主題1包含兩個對主題3的參照。 您可以選擇對應B作為第一個連結的父對應，選擇對應C作為第二個連結的父對應。

![舊版AEM Sites預設集](assets/aem-sites-legacy.png)

*從&#x200B;**AEM Sites**預設集的&#x200B;**交叉對應參考**索引標籤，指定連結主題的發佈內容。*

深入瞭解[AEM Sites預設集](../user-guide/generate-output-aem-site.md)。

### 為HTML5輸出選擇平面或巢狀檔案階層的選項

現在，Experience Manager Guides可讓您保留暫存檔的平面資料夾階層，其中整個內容會以HTML5輸出格式發佈，並儲存在單一資料夾中。
如果您不選擇平面化檔案階層，則會以巢狀資料夾階層產生HTML5輸出。 這表示內容的原始資料夾結構（其檔案會整理到子資料夾中）會在輸出中進行復寫。 此巢狀資料夾階層可以讓檔案的組織和分類更複雜，更易於管理和導覽大量資料。


深入瞭解如何[產生HTML5輸出](../user-guide/generate-output-html5.md)。


## 編輯器增強功能

2024.10.0版本已新增下列編輯器增強功能：

### 對鎖定檔案的作者和Source模式的唯讀存取權

如果DITA或Markdown檔案已由其他使用者鎖定或出庫，則您無法編輯或變更內容。 除了「預覽」以外，您也可以在「作者」或「Source」模式中以唯讀檔案的形式檢視它。
在唯讀模式中，您可以在**作者**&#x200B;或&#x200B;**Source**&#x200B;模式中檢視內容以及標籤和屬性，並編輯檔案屬性。

您也可以存取唯讀DITA map的&#x200B;**配置**&#x200B;檢視。
>[!NOTE]
>
> 您的資料夾設定檔管理員必須更新&#x200B;*ui_config.json*，以便您可以在「作者」、「Source」和「版面」模式中和諧地存取唯讀檔案。

![鎖定的檔案編輯器](./assets/locked-file-editor.png)
*在[作者]和[Source]模式中檢視鎖定的檔案。*


瞭解如何[在作者和Source模式中開啟鎖定的檔案](../user-guide/web-editor-edit-topics.md#open-locked-files-in-author-and-source-modes)。


### 增強內容組織的群組條件

Experience Manager Guides現在可讓您將條件分組，並以巢狀階層顯示條件，好讓您將多個條件新增至單一群組。 透過分組條件，您可在內容中更妥善地組織和套用條件。

以巢狀階層方式組織的![條件](assets/conditions-nested-hierarchy.png){width="300" align="left"}

在[左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS)區段中進一步瞭解&#x200B;**條件**&#x200B;功能說明。




