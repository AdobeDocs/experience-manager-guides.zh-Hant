---
title: 發行說明 | 已修正Adobe Experience Manager Guides 4.4.0版本中的問題
description: 瞭解Adobe Experience Manager Guides 4.4.0版的錯誤修正
role: Leader
source-git-commit: 8f8075b205725a55b93286c804b879353b4d965d
workflow-type: tm+mt
source-wordcount: '1434'
ht-degree: 0%

---

# 已修正4.4.0版（2024年1月）中的問題


本文介紹4.4.0版Adobe Experience Manager Guides中不同區域所修正的錯誤。

如需新功能和增強功能的詳細資訊，請檢視 [4.4.0版的新增功能](./whats-new-4-4.md).

瞭解 [4.4.0版的升級指示](../release-info/upgrade-instructions-4-4.md).


## 製作

- 編輯器中的拼字檢查不允許選擇建議。 (15045)
- 全域導覽按鈕無法運作，且儀表板無法載入。 (14968)
- 在網頁編輯器中，下載對應功能在準備下載時無法觸發快顯通知。 (14626)
- 在網頁編輯器中，下載對應功能無法下載包含基準的對應。 (14622)
- Experience Manager指南中的DTD錯誤無效。 (14482)
- Web編輯器索引標籤中的標題會在點(.)之後被截斷 設定的 Cookie。(14372)
- 資產UI中重複對應名稱的錯誤訊息未更新。 (14320)
- 拖放資產期間，版本建立邏輯中發生錯誤。 (14291)
- 可重複使用的內容會略過元素ID。 (14213)
- 要隱藏的設定控制項 **語言變數** 下的面板 **輸出** 索引標籤遺失。 (14194)
- 使用中的專用結構描述新增參考或主題時，Web編輯器擲回應用程式錯誤 **版面** 檢視。 (14094)
- conref後面的空格 `<ph>` 儲存主題時，元素會消失。 (13642)
- 嘗試在後處理完成之前儲存DITA檔案時發生應用程式錯誤。 (13571)
- 連結至的錨點 `<dlentry>` 或 `<dt>` 元素無法顯示連結文字。 (13543)
- 此 **我的最愛** Web編輯器中的集合無法載入。 (13495)
- 如果主題的標題包含斜線 `/`，網頁編輯器中的索引標籤只會顯示後面跟著的字母。 (13455)
- 在網頁編輯器中顯示預覽後，影像預覽並未消失。 (13454)
- 以含空格的唯一ID建立時，引文會顯示不可點按的連結。 (13447)
- 在編輯主題後關閉主題時，系統會將您重新導向至AEM首頁，而非返回資料夾檢視。 (13306)
- 在其他主題中使用根對映定義的索引鍵時，插入關鍵字快顯視窗沒有出現。 (12950)
- 在中預覽高度很大的圖形時，不會顯示關閉圖示 **版本記錄** 面板。 (12867)
- 無法修改的時區 **版本建立日期** 「基準線」欄。 (12711)
- 網頁編輯器中無法辨識Zip檔案，而且您無法拖放它們。 (12709)
- 此 **版本記錄** Assets UI中的面板會針對以下專案顯示不正確的時間戳記： **目前** 欄位。 (12624)
- 在 **版面** 檢視書籤，使用 **右移** 讓選取的章節成為子元素無法運作。 (12567)
- 從檔案名稱以數字字元開頭的範本建立DITA檔案會導致名稱空間錯誤。 (12188)
- 即使使用者未明確從「 」設定Rootmap，它仍會保留在網頁編輯器中。 **使用者偏好設定**. (11551)
- 已套用某些屬性的內容在中不會反白顯示 **作者** 或 **預覽** 模式。 (11063)
- 在網頁編輯器中， **重要參考資料** 視窗會在插入時開啟 `varname` 標籤之間。 (10940)
- 將字彙表主題從存放庫拖曳到字彙表對應中會建立 `topicref`. (10767)
- 在Google Chrome和Microsoft Edge瀏覽器中，XML編輯器的預覽視窗會遭截斷。 (10755)
- 網頁編輯器無法包裝可能上層元素內的元素。 (8791)
- 重新安裝Adobe Experience Manager Guides 4.3.1版後，Web編輯器會解除安裝。 (14519)
- 安裝程式4.3.1版遇到篩選器衝突，導致覆寫 `apps/cq/core/content/projects/properties`. (14517)
- 自我參照連結會出現在清單的下方 **中斷的連結** 在報表中。 (13539)
- 程式碼片段的預覽畫面會凍結。 (14840)
- 以韓文建立片段時會出現損壞的字元。 (13489)

## 發佈

- AEM Sites發佈失敗並導致下列檔案的範圍錯誤： `xref` 至以「HTTP」開頭的DITA檔案。 (15154)
- 在原生PDF發佈中，無法使用DITA map中繼資料屬性來填入PDF檔案輸出的中繼資料。 (15159)
- 在原生PDF發佈中，條件預設集中的自訂屬性不適用於原生PDF發佈。 (14943)
- 無法從新增自訂範本 **輸出** 索引標籤進行編輯。 (14846)
- **AEM網站** 預設集因空白範本路徑而無法運作。 (14804)
- 對於主題包含MathML方程式的DITA map，AEM網站重新產生失敗。 (14790)
- 在原生PDF發佈中，PDF產生會在取得的相依性時擲回錯誤 `Node.js` 發佈。 (14445)
- **AEM網站** 預設集不允許選取外部的範本 `/content` 網頁編輯器中的階層。 (14260)
- 發佈為內容片段的功能不適用於搜尋結果中列出的檔案。 (14090)
- Fmdita元件的硬式編碼路徑為 `delegator.jsp`，防止AEM Sites元件覆蓋。 (13993)
- 原生PDF發佈輸出中PDF反應器的標籤檢視未按預期運作。 (13622)
- 在原生PDF發佈中， **範本** 佈局需要在恢復為時重新載入頁面 `None`. (13621)
- AEM網站發佈在具有範圍對等連結的大型地圖提交到資料存放區時遇到問題。 (13531)
- 在AEM網站發佈中，在具有範圍對等連結的大型DITA map認可資料存放區時發生問題。 (13530)
- 顯示的圖示和工具提示不正確  **編輯內容** 中的選項 **頁面配置** 用於原生PDF發佈的範本工具列。 (13492)
- 無法使用「Experience Manager指南」啟用網站 **大量發佈儀表板**. (13439)
- 在原生PDF發佈中，由於頁首和頁尾中的影像不顯示替代文字，導致協助工具受損。 (12829)
- 在AEM Sites輸出中，的樣式或分行符號遺失 `<lines>` 具有子元素的元素。(12542)
- 若沒有自動新增的副檔名，以原生PDF複製頁面版面配置將無法運作。 (12534)
- 元素標籤本地化在AEM Sites輸出中無法正常運作。 (12144)
- 自訂中繼資料無法在最終輸出中使用。 (12116)
- `fmdita rewriter` 與使用者的重寫程式設定衝突，並導致顯示長URL而不是連結。 (12076)
- 遺失 **ditaval** 透過Web編輯器UI建立的資料夾設定檔層級輸出預設集中的選項。 (11903)
- 在 **AEM網站**  預設集，選項為 **為每個主題產生個別PDF** 無法運作。 (11555)
- 原生PDF發佈不支援CMYK色域轉換。 (10754)
- 升級至4.3.1版時，原生PDF節點中會發生一些例外狀況。 (14492)
- 使用原生PDF發佈產生PDF輸出時，檔案名稱會在句點後截斷。 (13620)


## 管理

- 複製貼上具有不含GUID的自參照連結的DITA檔案時，內容參照會中斷。 (13540)
- **基線篩選** 檔案無法在網頁編輯器中使用檔案名稱。 (13486)
- 在Web編輯器中，基準線顯示先前版本（而非選取的DITA檔案版本）的標題。 (13444)
- 停用父DITA map的索引以獲得更好的效能可能會影響某些功能的功能。(12213)
- 未建立大型DITA map的條件預設集。 (10936)
- 編輯地圖集合時，無法編輯集合中第一個地圖的預設集。 (10649)
- 標籤來自 `labels.json` 檔案會以隨機順序出現在網頁編輯器中。 (10508)
- 動態基準線呼叫使用名稱而非標題，導致匯出DITA map API失敗。 (14268)

## 檢閱

- 右鍵快顯功能表無法用於 **Accept** 或 **拒絕** 追蹤變更。 (14607)
- 在Adobe Experience Manager Guides 4.3.1版中，在檢閱畫面中切換以關閉DITA主題無法運作。 (14537)
- 在Web編輯器中，先前和目前版本的並排檢閱面板會發生對稱問題。 (14156)
- 自訂稽核工作流程的電子郵件範本不適用於覆蓋。 (13954)
- Experience Manager指南稽核畫面中的韓文附件無法點選。 (13436)
- 在檢閱和共同作業畫面中，地圖示題遭到切斷，沒有檢視完整標題的選項。 (13012)

## 轉換

- 此 **接受/拒絕** 自動核准的人工翻譯按鈕出現錯誤。 (14318)
- 將非英文DITA檔案轉換成AEM頁面時，會發生國際化(i18n)問題。 (14286)
- 自動核准有時無法運作，且若上設定的值不正確，則會發生例外 **翻譯狀態**. (13607)
- 從「翻譯」儀表板匯出的基線會失敗，且不會以目標語言開啟。 (12993)
- 已翻譯內容無法從臨時翻譯專案同步，且DITA XML編輯器翻譯精靈顯示不正確 **進行中** 已核准工作的狀態。 (9938)

## 已知問題

Adobe已發現4.4.0版的下列已知問題：

- 1.0版不會顯示在重複DITA檔案的UI上。