---
title: 適用於原生PDF的新發佈引擎 | PDF輸出產生
description: 瞭解如何使用全新的發佈引擎進行原生PDF發佈
feature: Publishing, Native PDF Output
role: User
TQID: https://experienceleague.adobe.com/GV3iYtBdFVrQwFjdvfqnfDIWPMugO3hFjS4FZqspG2M
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
  - id: afb45297-4313-4f67-818e-bc0b03abe086
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: d6596f3f-92a7-43ec-b444-237db6adad05
  - id: f6b497f1-f8e0-42ce-8e95-56c28d94026e
  - id: f9dbea21-a714-40dd-bc90-080d8046c93f
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: cc72dcf1-72e1-48cc-b434-e7c27d62d67c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 010a11e20d518064549ce7d66648586f49f572ec
workflow-type: tm+mt
source-wordcount: 913
ht-degree: 0%

---

# 使用原生PDF引擎v2

新發佈引擎&#x200B;*原生PDF引擎v2*&#x200B;是以升級的PDF產生架構為基礎，並包含字型處理、CSS處理和轉譯行為的變更。

因此，使用新發佈引擎產生的PDF輸出可能會與使用現有PDF引擎產生的輸出不同（*原生PDF引擎v1*）。 在文字版面、間距、樣式、影像演算和註腳格式設定等區域中，可能會顯示差異。

例如，原生PDF引擎v2支援`OpenType`字型，而原生PDF引擎v1主要依賴`TrueType`字型。 類似的彩現增強功能可能會影響所產生PDF的整體外觀。

如需如何在您的環境中啟用原生PDF引擎v2的詳細資訊，請檢視[為原生PDF設定新的發佈引擎](./conf-new-pdf-engine.md)。

## 建議新發佈引擎的CSS更新

如果您想保留原生PDF引擎v1在使用原生PDF引擎v2時產生的PDF輸出外觀，您可能需要更新自訂CSS。 底下所述的建議CSS變更有助於在啟用新設定後維持輸出一致性。

| 說明 | 建議的CSS更新 |
|-------------|------------------------------------------------|
| 縮放的影像可能會因為影像演算行為中的變更而呈現不同的外觀。 | 若要還原影像演算行為，請新增： <br><br><pre><code>&quot;&#39;css
影像演算：畫素化；

```</code></pre> |
| 目錄導線(TOC)對齊方式可能會因為導線的演算行為發生變更而顯示稍有不同。 | 若要恢復目錄導線對齊，請調整自訂樣式表中目錄導線元素的樣式。 所需的CSS變更可能會因您的目錄版面配置和格式而異。 |
| 由於字型演算和字元版面配置處理的變更，文字間距和繞線可能會有所不同。 | 如果您的樣式表使用`sans-serif`字型系列或顯示間距差異的字型，請新增：<br><br><pre><code>&quot;&#39;css
內文{ -ro-glyph-layout-mode： quality； }
```</code></pre> |

| 由於預設註腳樣式的變更，註腳參照可能不會再顯示為上標標籤。 | 若要還原上標樣式的註腳標籤，請新增：<br><br><pre><code>&quot;&#39;css
.fn：：footnote-marker &lbrace;
  內容：計數器（註腳） &quot; &quot;；
  vertical-align： super；
  font-size： 65%；
&rbrace;

```</code></pre> |
| 由於底線位置的變更，底線文字與底線之間的間距可能會增加。 | 若要還原底線位置，請使用`text-underline-offset`屬性，並視需要調整位移值。 例如：<br><br><pre><code>&quot;&#39;css
文字裝飾：加底線；
text-underline-offset： -0.1em；
```</code></pre> |

| 清單標籤和清單專案文字之間的間距可能會因為清單演算行為的變更而有所不同。 | 若要恢復間距，請增加清單專案的左內距。 例如：<br><br><pre><code>&quot;&#39;css
.step &lbrace;
  頂端邊界： 0.3rem；
  下邊界：0.5rem；
  左內邊距： calc(1.5rem + 1ch)；
&rbrace;

```</code></pre> |
| 標題前的間距可能會因為邊界收合行為的變更而有所不同。 | 若要恢復間距，請檢閱相鄰元素的邊界，並視需要減少或移除重疊的上邊界和下邊界。 例如：<br><br><pre><code>&quot;&#39;css
h1.chapter { margin-top： 0； }
.chaptoc-body { margin-bottom： 0； }
```</code></pre> |

| 由CSS產生的核取記號標籤可能會以不同的大小或樣式出現，因為它們會使用不同的遞補字型來呈現。 | 若要一致地呈現標籤，請使用包含兩個字元的字型系列。 例如：<br><br><pre><code>&quot;&#39;css
：：marker &lbrace;
  font-family： -ro-symbols ！important；
&rbrace;

```</code></pre> |
| CSS產生的圓形清單標籤可能會因為標籤定位行為的變更而出現部分裁剪或截斷。 | 若要恢復圓形清單標籤的外觀，請避免使用標籤的絕對定位。 如果需要絕對定位，請明確指定適當的`top`值，以正確定位標籤。 |
| 當清單專案使用`position: relative`等定位樣式時，PDF/UA輸出中的清單專案讀取順序可能會有所不同。 | 若要讓閱讀順序更密切地遵循來原始檔結構，請套用下列CSS屬性至清單專案： <br><br><pre><code>&quot;&#39;css
li {
  -ro-paint-reordering：避免；
}
```</code></pre> |


## 已知問題的因應措施

使用原生PDF引擎v2時，下列因應措施可協助解決產生PDF輸出中的已知問題。

- 套用至資料表內容的`text-decoration` css屬性沒有在PDF輸出中轉譯。

  **因應措施**：將文字裝飾屬性套用至表格內容中的`span`元素，而非直接套用至表格元素。

- `-ro-colorbar-top-left`和`-ro-colorbar-top-right` CSS屬性不會影響PDF輸出中的色彩列。

  **因應措施**：從`mergedHTML.json`中的使用者樣式表中移除對應的值，或將`!important`新增至檔案CSS中的屬性值，以便使用者樣式表不會覆寫這些值。

- 當頁面寬度受限時，色列可能會合併出現，因為色列沒有隨著PDF輸出中的頁面大小縮減。

  **因應措施**：在頁面的不同側邊顯示灰色和彩色列，或是調整色列設定，使它們在較小的頁面寬度上不會重疊。

## 修正新發佈引擎的問題

使用&#x200B;_原生PDF引擎v1_&#x200B;產生的PDF輸出中的下列問題已在&#x200B;_原生PDF引擎v2_&#x200B;中修正：

- 為特定內容產生原生PDF輸出時，儘管中間HTML包含多個頁面的完整內容，PDF中仍只會轉譯第一個頁面。 (GUIDES-28270)
- 已啟用協助工具設定之原生PDF輸出內容的讀取順序不正確。 頁尾的頁碼會在主要內容之前讀取，而不是在結尾讀取。 (GUIDES-27790)
- 原生PDF輸出中的色彩列不會延伸至整個頁面寬度，且在自訂頁面大小時重疊，導致某些色彩方塊隱藏。 (GUIDES-15505)
- 原生PDF輸出中不遵循`CSS:is()pseudo-class`選擇器，導致與瀏覽器呈現的樣式不同。 (GUIDES-11328)