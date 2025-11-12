---
title: 發行說明 | 已修正2025.11.0版Adobe Experience Manager Guides中的問題
description: 瞭解Adobe Experience Manager Guides as a Cloud Service 2025.11.0版中的錯誤修正。
source-git-commit: d9a46a009477b1110208a509d4ad8c0616139661
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 3%

---

# 已修正2025.11.0版本中的問題

本文介紹2025.11.0版Adobe Experience Manager Guides as a Cloud Service中不同區域修正的錯誤。

如需新功能和增強功能的詳細資訊，請參閱 [2025.11.0 版本中的新增功能](whats-new-2025-11-0.md)。

瞭解2025.11.0版[的](upgrade-instructions-2025-11-0.md)升級指示。

## 製作

- 如果將沒有屬性或值的空白`prop`元素新增到DITAVAL檔案，則無法新增其他`prop`元素。 (GUIDES-33597)
- 將Experience Manager Guides升級至2025.08.0版後，**Workspace設定**&#x200B;中不再顯示啟用或停用自訂&#x200B;**Acrolinx**&#x200B;索引標籤的選項。 (GUIDES-35261)
- 在瀏覽器重新整理時，在主題或地圖的資料夾層級設定檔中套用的自訂CSS將恢復為預覽模式的預設樣式。 (GUIDES-31098)
- 在DITA檔案編輯器的Source檢視中，**復原**&#x200B;和&#x200B;**取消復原**&#x200B;作業無法如預期運作。 (GUIDES-24914， GUIDES-25034)
- 使用`Xref`元素在主題中參照DITA map時，會顯示參照之對應的檔案名稱，而非對應的標題。 (GUIDES-21759)
- 透過Editor介面的右側面板新增多個Schematron檔案以進行驗證時，即使新增的檔案有效且沒有錯誤，也會顯示錯誤&#x200B;**Schematron檔案不存在或存在錯誤**。 (GUIDES-33731)
- 大型或複雜的MathML方程式無法在編輯器中顯示。 (GUIDES-29095)

## 資產管理

- 當您透過Experience Manager Guides UI重新上傳已編輯的影像時，影像的原始轉譯會更新，但相關的DITA內容會繼續顯示影像的先前版本。 (GUIDES-33693)
- 嘗試將兩個或多個資料夾從其來源位置移動至不同位置時（使用「大量移動工具」），如果資料夾名稱以相同字串開頭（例如Product和ProductImages），作業會失敗。 (GUIDES-29096)
- 從Omnisearch Assets UI刪除搜尋的資產，會略過&#x200B;**強制刪除**&#x200B;警告對話方塊並直接刪除資產，即使資產已在現有DITA內容中參考亦然。 (GUIDES-17232)

## 發佈

- 在AEM Sites上使用基準線（搭配舊版元件對應）發佈DITA map時，也會發佈具有屬性`processing-role = resource-only`的map元素。 (GUIDES-37649)
- 在某些情況下，在AEM Sites輸出頁面（具有舊版元件對應）中發現`jcr:content/fmUuidOfSource`屬性遺失，導致新建立的內容頁面無法探索。
- 透過DITAVal篩選器和條件預設集進行內容篩選不適用於Salesforce發佈。 (GUIDES-33515)
- 如果內容階層中存在相同名稱的資料夾，則無法為地圖建立原生PDF預設集。 (GUIDES-33012)
- 當使用動態基準產生原生PDF輸出時，字詞&#x200B;**PDFProject**&#x200B;會顯示為PDF標題，而非實際地圖示題。 (GUIDES-31102)
- 在主題參考中產生具有特定`print`屬性值的原生PDF輸出無法如預期運作。 (GUIDES-31101)
- 使用Assets UI或&#x200B;**大量移動**&#x200B;選項移動包含DITA map的資料夾時，無法載入參照這些對應的現有對應集合和大量啟用集合。 (GUIDES-28355)
- 當您移動包含具有條件預設集之對映的資料夾時，移動後不會將條件套用至產生的輸出。 (GUIDES-28352)
- 當您使用舊版元件對應產生AEM Sites輸出時，使用`copy-to`屬性的主題會以`copy-from`主題的名稱（而不是`copy-to`屬性中設定的名稱）發佈。 (GUIDES-22155)
- 從&#x200B;**大量發佈儀表板**&#x200B;啟動一或多個DITA map會產生超大記錄。 (GUIDES-20746)

## Platform

- 透過Assets UI上傳資產或從編輯器介面建立新檔案時產生的錯誤記錄，在記錄訊息中錯誤使用字詞`predecessor`而非`successor`。 (GUIDES-35607)

## 已知問題

Adobe已找出下列2025.11.0版的已知問題：

- 使用`copy-to`屬性建立重複主題並使用`scope=peer`屬性參考該主題，會導致AEM Sites輸出中的重新導向問題，其中連結會從AEM Sites （使用複合元件對應）重新導向至AEM Sites （使用舊版元件對應），反之亦然。 (GUIDES-37656)











