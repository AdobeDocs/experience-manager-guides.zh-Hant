---
title: 發行說明 |修正2024.06.0版Adobe Experience Manager Guides中的問題
description: 瞭解Adobe Experience Manager Guides as a Cloud Service 2024.06.0版中的錯誤修正。
exl-id: 608e5b2c-72af-4498-9b63-935e698231d4
TQID: https://experienceleague.adobe.com/PWXSeB-BhL9Gc104XoVpfqdWqywq7T6bphx8im92C4c
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6id: c6d09140-3c91-45d3-b7ed-b681af752f43id: d90290ec-3e61-4ebd-8649-bcafe0836803
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: d4f22c6d-7923-41e5-9da3-527ff8df4bc8id: d6596f3f-92a7-43ec-b444-237db6adad05id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0efid: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 781
ht-degree: 8%

---

# 2024.06.0版中的已修正問題

本文介紹2024.06.0版Adobe Experience Manager Guides as a Cloud Service中不同區域修正的錯誤。

如需新功能和增強功能的詳細資訊，請參閱 [2024.06.0 版本中的新增功能](whats-new-2024-06-0.md)。

瞭解2024.06.0版](upgrade-instructions-2024-06-0.md)的[升級指示。

## 製作

- 超過15KB之主題的複製和貼上作業失敗，並出現非預期的錯誤。 (17171)
- 從&#x200B;**檔案屬性**&#x200B;面板變更檔案狀態的功能無法正常運作，且會變更為&#x200B;*草稿*&#x200B;狀態。 (17088)
- 使用自訂資料夾設定檔變更XML編輯器設定時，`ui_config.json`會以不正確的檔案更新。 (17011)
- 在&#x200B;**存放庫**&#x200B;面板中，重新開啟&#x200B;**進階篩選器**&#x200B;對話方塊時，**篩選器**&#x200B;搜尋不會保留&#x200B;**簽出者**&#x200B;欄位的值。 (16935)
- 建立版本後，主題中的連結影像無法顯示在基準線中。 (16931)
- 當&#x200B;**使用者偏好設定**&#x200B;設定為以&#x200B;**檔案名稱**&#x200B;檢視檔案時，可重複使用的內容面板不會列出元素。 (16896)
- 資料表標題專案中的子專案無法在Experience Manager Guides的&#x200B;**預覽**&#x200B;模式中呈現。 (16691)
- 由於&#x200B;**FileNotFoundException**&#x200B;例外狀況，Postprocess指令碼執行失敗。 (16517)
- Vimeo影片不支援Experience Manager Guides中的全熒幕功能。 (15996)
- 在`<pre>`或`<codeblock>`元素中貼上較長的預先格式化文字序列會導致文字被截斷。 (15859)
- 當範本透過程式碼安裝但保持未處理狀態時，由於重複的GUID會發生內容刪除。 (15858)
- Experience Manager Guides無法在&#x200B;**預覽**&#x200B;模式中遵守&#x200B;**處理角色**&#x200B;屬性。 (15787)
- 編輯器會斷斷續續地刪除所選區域以外的額外文字。  (15708)
- 無法從Word檔案或HTML複製大型表格並貼到網頁編輯器中。 (15369)
- Experience Manager Guides as a Cloud Service中的空白資料夾的&#x200B;**複製**&#x200B;函式失敗。 (15353)
- 缺少API或事件來擷取元素中新增的屬性或新元素的插入。 (15351)
- 無法在Web編輯器的`<ol>`標籤中新增`<data>`標籤。 (15161)
- 啟用Unified Shell時，**版本標籤管理**&#x200B;對話方塊會針對沒有標籤的版本錯誤顯示&#x200B;**主要內容**。 (15039)
- 大型檔案在網頁編輯器中載入緩慢，延遲幾秒鐘。 (14958)
- 在文字內的表格儲存格中按&#x200B;**Enter**&#x200B;鍵無法如預期分割段落。 (14251)
- 使用自動縮排功能後，Experience Manager DITA Guide無法觸發&#x200B;**儲存**&#x200B;功能。 (16482)
- 評論主題未以正確順序顯示。 (16319)
- 在&#x200B;**作者**&#x200B;檢視中，使用不斷行空格時發生複製並貼上問題，導致文字溢位。 (15541)

- 在`<topicmeta>`內的`<othermeta>`元素中，將`<conref>`新增至其他DITA map時，也會將地圖ID與元素的識別碼一起附加。 (15226)
- 進行變更時，無法從&#x200B;**屬性**&#x200B;面板更新`<conref>`。 (15209)
- 在表格儲存格中選取影像時，會選取整個儲存格。 (15188)

## 發佈


- 互動對應連結無法在具有`peer @scope`之連結的發佈內容設定中顯示所有父對應。 (16700)
- 新增或移除任何現有屬性時，**條件預設集**&#x200B;會保留舊屬性。 (15890)
- 原生PDF發佈輸出中的RTL語言內容處理不正確。 (15709)
- 產生原生PDF輸出時，不會建立第一個PDF的版本。 (10305)
- 在原生PDF中，巢狀DITA主題在目錄(TOC)中無法正確顯示。 (16742)
- 從Dynamic Media針對視訊檔案產生的縮圖無法保留在發佈的輸出中。 (15656)
- 在ARM64處理器上產生原生PDF Publishing的輸出失敗。 (16968)

## 管理

- 編輯現有基準線並選取特定版本會觸發應用程式錯誤。 (14451)

## 翻譯

- 翻譯專案無法在2023年10月發行的Adobe Experience Manager 6.5 SP18中新增語言工作。 (15398)

## Cloud Service

- Adobe Experience Manager工具導覽無回應。 (17118)
- 雲端服務部署中的組建轉換階段因來自DITA程式碼基底的錯誤而失敗。 (14432)

## 報告

- 由於複製DITA資產時未修補的屬性，Experience Manager Guides UI中的&#x200B;**主題清單**&#x200B;計數不正確，這會影響為DTIA map產生的報表。 (15529)
- 包含URL中具有&#x200B;*%20*&#x200B;的外部參照的主題會顯示損毀的檔案參照。 (15347)


## 已知問題

Adobe已找出下列2024.06.0版的已知問題：

- 將Vimeo內容新增至主題時，原生PDF發佈會失敗。
- 在頁面配置的中繼資料欄位中，未依照選取的格式顯示&#x200B;**主題屬性**。
- 啟用Dynamic Media時，**Assets**&#x200B;檢視中無法點選`xrefs`。
