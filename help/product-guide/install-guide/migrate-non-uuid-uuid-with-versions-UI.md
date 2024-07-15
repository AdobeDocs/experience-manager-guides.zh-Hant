---
title: 從使用者介面將具有版本的非UUID內容轉換為UUID內容
description: 瞭解如何使用4.3.x版本移轉非UUID內容。
source-git-commit: f18c19eb493cd4d2003f68b082e71ebe7b3e6b7a
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---

# 透過使用者介面的版本移轉非UUID內容

如果您是使用4.3.x版或更新版本，請執行這些步驟，將具有版本的非UUID內容移轉至UUID內容。

## 相容性矩陣

| 目前的AEM Guides版本（非UUID） | 移轉至UUID的必要版本 | 支援的升級路徑 |
|---|---|---|
| 4.3.x或更新版本 | 4.3.0非UUID | 安裝4.3.1 (UUID) |

## 必要的套件

1. **版本清除**： `com.adobe.guides.version-purge-1.0.11.zip` （選擇性）
1. **移轉前**： `com.adobe.guides.pre-uuid-migration-1.1.2 .zip`
1. **移轉**： `com.adobe.guides.uuid-upgrade-1.1.13.zip`



## 移轉前

1. （可選）對內容執行版本清除以移除不必要的版本，並加快移轉程式。 若要在4.1版上執行版本清除（4.0版不支援），請安裝套件`com.adobe.guides.version-purge-1.0.11.zip`，並使用此URL `http://<server-name> /libs/fmdita/clientlibs/xmleditor_version_purge/page.html`移至使用者介面。

   >[!NOTE]
   >
   >此公用程式不會移除基準線或評論中使用的任何版本，或具有任何標籤。
1. 安裝移轉前套件(`ccom.adobe.guides.pre-uuid-migration-1.1.2 .zip`)。

   >[!NOTE]
   >
   >* 您需要管理員許可權才能執行移轉。
   >* 建議先修復有錯誤的檔案，再繼續移轉。

1. 從左側面板選取&#x200B;**相容性評估**，並瀏覽資料夾路徑。
1. 檢查相容性以列出以下資訊：
   * 檔案總數
   * 總版本
   * 預估移轉時間
   * 有錯誤的檔案數



移轉中的![相容性評估標籤](assets/migration-compatibility-assessment.png){width="800" align="left"}


1. 從左側面板中選取&#x200B;**設定驗證**。 然後&#x200B;**選取對映**&#x200B;和&#x200B;**選取對映的預設集**&#x200B;以進行設定。 目前的輸出驗證清單將顯示移轉前存在的輸出檔案，並可在稍後針對移轉後產生的輸出檔案進行驗證。

![在移轉中設定[驗證]索引標籤](assets/migration-configure-validation.png){width="800" align="left"}




## 移轉

### 步驟1：更新設定

1. 請確定可用的空間至少是AEM （crx-quickstart目錄）在移轉期間所佔用空間的10倍。 完成移轉後，您可以執行壓縮來回收大部分的磁碟空間（請參閱[修訂清理](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=en)）。

1. 啟用&#x200B;*在`com.adobe.fmdita.config.ConfigManager`中啟用Post處理工作流程啟動器*，並在`com.adobe.fmdita.postprocess.version.PostProcessVersionObservation.`中啟用&#x200B;*版本後處理*

1. 安裝支援發行版本的UUID版本，而非非UUID版本。 舉例來說，如果您使用4.0版的非UUID組建或4.1版的非UUID組建，便需要安裝UUID 4.1版。

1. 安裝新的套件以進行uuid移轉(`com.adobe.guides.uuid-upgrade-1.1.13`)。

1. 停用下列工作流程，以及使用`http://localhost:4502/libs/cq/workflow/content/console.html`中的啟動器在`/content/dam`上執行的任何其他工作流程。

   * DAM更新資產工作流程
   * dam中繼資料回寫工作流程

1. 停用&#x200B;*啟用`com.adobe.fmdita.config.ConfigManager`中的Post處理工作流程啟動器*，並停用`com.adobe.fmdita.postprocess.version.PostProcessVersionObservation`中的&#x200B;*啟用版本後處理*。

1. 停用Day CQ Tagging Service中的Enable validation (`validation.enabled`)屬性。

1. 請確定`com.adobe.fmdita.config.ConfigManager`中的`uuid.regex`屬性資料夾已正確設定。 如果空白，請將其設定為預設值 — `^GUID-(?<id>.*)`。
1. 為`com.adobe.fmdita.uuid.upgrade.UuidUpgrade`新增個別的記錄器瀏覽器回應也可在`/content/uuid-upgrade/logs`取得。

### 步驟2：執行移轉並驗證

#### 安裝移轉套件

![移轉中的系統升級索引標籤](assets/migration-system-upgrade.png){width="800" align="left"}

* 從左側面板選取&#x200B;**系統升級**&#x200B;以執行移轉。 先從資料夾中較小的資料開始，再於`/content/dam`上執行。

* 在移轉執行時選取[下載報表] **，檢查資料夾中的所有檔案是否已正確升級，以及所有功能是否只適用於該資料夾。**


>[!NOTE]
>
> 內容移轉可在資料夾層級或完整`/content/dam`上執行，或在相同資料夾上執行（重新執行移轉）。

此外，請務必確實針對所有媒體資產完成內容移轉，例如您在DITA內容中使用的影像和圖形。

#### 基準線及檢閱移轉

從左側面板選取&#x200B;**基準線/檢閱升級**，以移轉基準線並在資料夾層級檢閱。

![移轉中的基準與檢閱索引標籤](assets/migration-baseline-review-upgrade.png){width="800" align="left"}


### 步驟3：還原設定

伺服器成功移轉後，請啟用後續處理、標籤和下列工作流程（包括移轉期間最初停用的所有其他工作流程）以繼續在伺服器上運作。

* DAM更新資產工作流程
* DAM中繼資料工作流程

>[!NOTE]
>
>如果某些檔案在移轉前未處理或損毀，則會在移轉前損毀，甚至在移轉後仍會損毀。

## 移轉驗證

移轉完成後，請從左側面板選取&#x200B;**驗證系統升級**，並在移轉前後驗證輸出檔案，以確保移轉成功。

![在移轉中驗證系統升級索引標籤](assets/migration-validate-system-upgrade.png){width="800" align="left"}


1. 完成移轉後，可以執行壓縮來回收大部分的磁碟空間（請參閱`https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=en`）。

