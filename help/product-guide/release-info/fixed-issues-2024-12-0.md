---
title: 發行說明 | 已修正2024.12.0版Adobe Experience Manager Guides中的問題
description: 瞭解Adobe Experience Manager Guides as a Cloud Service 2024.12.0版中的錯誤修正。
exl-id: 04a57e1a-6e74-46f6-acde-5045d3dcacdc
source-git-commit: dd404c42863f0b4a5f31b54f770c0bf296d68ab9
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 1%

---

# 已修正2024.12.0版本中的問題

本文介紹2024.12.0版Adobe Experience Manager Guides as a Cloud Service中多個區域修正的錯誤。

瞭解2024.12.0版[&#128279;](./upgrade-instructions-2024-12-0.md)的升級指示。

## 製作

- 在`XMLEditorConfig`中啟用`xmleditor.uniquefilenames`時，無法在UUID執行個體上建立DITA map。 (21201)
- 關閉檔案時，**儲存變更及解除鎖定檔案**&#x200B;對話方塊中新增的註解和標籤沒有以新版本儲存在「版本記錄」中。 這是特定使用案例，其在`XMLEditorConfig`中啟用了&#x200B;**Ask for Check in Close**&#x200B;或&#x200B;**Ask for New Version on Close**。 (20065)
- 儲存新版本之前，標籤為&#x200B;**完成**&#x200B;的檔案狀態會回覆成&#x200B;**草稿**，導致&#x200B;**完成**&#x200B;狀態不會持續存在於任何檔案版本中。 (20006)
- 無法在網頁編輯器的主題中新增PDF檔案作為影像參考。 (21206)
- 在Assets UI中選取DITA檔案會顯示&#x200B;**在FrameMaker中開啟**&#x200B;選項，即使在組態中停用亦然。 (20082)

## 發佈

- 在原生PDF輸出中，目錄中有章節標題遺失，導致不正確的階層。 (21840)


## 管理

- 因為記錄檔中有&#x200B;**個未關閉的ResourceResolver**&#x200B;錯誤，所以發生資源洩漏。 (18488)
- 建立新的或重複的基準線時，標籤會以隨機順序顯示。 (19307)


## 基準線

- 如果基線具有大量主題或地圖，請在1分鐘後編輯並在雲端設定上儲存基線並逾時。 (19558)

## 翻譯

- 使用基線的地圖轉譯會變得緩慢，最終無法載入所有關聯主題和地圖檔案的清單。 (19733)

## 因應措施的已知問題

Adobe已在2024.12.0版的Adobe Experience Manager Guidesas a Cloud Service中找出下列已知問題。

**處理內容翻譯時專案建立失敗**

傳送內容以供翻譯時，專案建立會因下列記錄錯誤而失敗：

處理翻譯專案時發生`com.adobe.cq.wcm.translation.impl.TranslationPrepareResource`錯誤

`com.adobe.cq.projects.api.ProjectException`：無法建立專案

原因為： `org.apache.jackrabbit.oak.api.CommitFailedException`： `OakAccess0000`：存取遭拒


**因應措施**：若要解決此問題，請執行下列因應措施：

1. 新增repoinit檔案。 如果檔案不存在，請執行[範例repoinit設定建立步驟](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-cloud-questions/repoinit-configuration-for-property-set-on-aem-as-cloud-service/m-p/438854)來建立檔案。
2. 在檔案中新增下列行並部署程式碼：

   ```
   { "scripts": [ "set principal ACL for translation-job-service\n allow jcr:all on /home/users/system/cq:services/internal/translation\nend" ] }
   ```

3. 部署後測試翻譯。

