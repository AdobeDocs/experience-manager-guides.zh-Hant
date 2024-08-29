---
title: 將具有版本的非UUID內容轉換為UUID內容
description: 瞭解如何將具有版本的非UUID內容移轉至UUID內容。
feature: Migration
role: Admin
level: Experienced
exl-id: 8f3a89fc-7d18-453d-909d-6dff5e275cab
source-git-commit: b0c7b944b66c4a4167beece4f827f3d5789531b5
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---

# 移轉受版本控制的內容

>[!NOTE]
>
> 您可以將非UUID內容移轉至Experience Manager Guides中的UUID內容。 本文將會在2024年11月封存。
>檢視&#x200B;[**非UUID到UUID內容移轉**](./migrate-non-uuid-uuid-new.md)，以取得最新和詳細檔案。

執行這些步驟，將您的非UUID版本化內容移轉至UUID內容。

>[!NOTE]
>
>請依照產品授權版本專屬的[升級指示](./upgrade-xml-documentation.md)執行。

## 相容性矩陣

| 目前的Experience Manager Guides版本（非UUID） | 移轉至UUID的必要版本 | 支援的升級路徑 |
|---|---|---|
| 3.8.5、4.0.x或4.1.x | 4.1非UUID | 安裝4.1 (UUID)並執行移轉 |
| 4.2、4.2.x或4.3 | 4.3.0非UUID | 安裝4.3.1 (UUID)並執行移轉 |
| 4.3.1 | 不適用 | 不適用 |

## 套件安裝

根據您的版本，從Adobe軟體發佈入口網站下載必要的套件：
<details>
<summary>  版本4.1的套件升級路徑</summary>

1. **移轉前**： [com.adobe.guides.pre-uuid-migration-1.0.9.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2Fother-packages%2Fuuid-migration%2F1-0%2Fcom.adobe.guides.pre-uuid-migration-1.0.9.zip)
1. **移轉**： [com.adobe.guides.uuid-upgrade-1.0.19.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2Fother-packages%2Fuuid-migration%2F1-0%2Fcom.adobe.guides.uuid-upgrade-1.0.19.zip)
</details>


<details>
<summary> 版本4.3.1的套件升級路徑</summary>

1. **移轉前**： [com.adobe.guides.pre-uuid-migration-1.1.3.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2Fother-packages%2Fuuid-migration%2Fcom.adobe.guides.pre-uuid-migration-1.1.3.zip)
1. **移轉**： [com.adobe.guides.uuid-upgrade-1.1.15.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2Fother-packages%2Fuuid-migration%2Fcom.adobe.guides.uuid-upgrade-1.1.15.zip)

</details>

## 移轉前

對非UUID版本（非UUID 4.1或非UUID 4.3.0）執行下列檢查：

1. 根據您的版本安裝移轉前套件。

   >[!NOTE]
   >
   >* 您需要管理員許可權才能執行移轉。
   >* 建議先修復有錯誤的檔案，再繼續移轉。

1. （可選）對內容執行版本清除以移除不必要的版本，並加快移轉程式。 若要執行版本清除，請從移轉畫面中選取選項&#x200B;**版本清除**，然後使用URL `http://<server- name>/libs/fmdita/clientlibs/xmleditor_uuid_upgrade/page.html`移至使用者介面。
   >[!NOTE]
   >
   >此公用程式不會移除基準線或評論中使用的任何版本，或具有任何標籤。

1. 啟動`http://<server-name>/libs/fmdita/clientlibs/xmleditor_uuid_upgrade/page.html`。
1. 從左側面板選取&#x200B;**相容性評估**，並瀏覽資料夾路徑。
1. 檢查相容性以列出以下資訊：
   * 檔案總數
   * 總版本
   * 預估移轉時間
   * 有錯誤的檔案數

   移轉中的![相容性評估標籤](assets/migration-compatibility-assessment.png){width="800" align="left"}


1. 從左側面板中選取&#x200B;**設定驗證**。 然後，**選取對映**&#x200B;和&#x200B;**選取對映的預設集**&#x200B;以進行設定。 目前的輸出驗證清單會顯示移轉前存在的輸出檔案，並可在稍後針對移轉後產生的輸出檔案進行驗證。

   ![在移轉中設定[驗證]索引標籤](assets/migration-configure-validation.png){width="800" align="left"}




## 移轉

### 步驟1：更新設定

1. 請確定可用的空間至少是AEM （crx-quickstart目錄）在移轉期間所佔用空間的10倍。 完成移轉後，您可以執行壓縮來回收大部分的磁碟空間（請參閱[修訂清理](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=en)）。

1. 啟用&#x200B;*在`com.adobe.fmdita.config.ConfigManager`中啟用後處理工作流程啟動器*，並在`com.adobe.fmdita.postprocess.version.PostProcessVersionObservation.`中啟用&#x200B;*版本後處理*

1. 安裝支援發行版本的UUID版本，而非非UUID版本。 例如，如果您使用4.1非UUID版本編號，則需安裝UUID 4.1版並執行移轉。

1. 安裝新套件以進行uuid移轉。

1. 停用下列工作流程，以及使用`http://<server-name>/libs/cq/workflow/content/console.html`中的啟動器在`/content/dam`上執行的任何其他工作流程。

   * DAM更新資產工作流程
   * dam中繼資料回寫工作流程

1. 停用`com.adobe.fmdita.config.ConfigManager`中的&#x200B;*啟用後處理工作流程啟動器*，並停用`com.adobe.fmdita.postprocess.version.PostProcessVersionObservation`中的&#x200B;*啟用版本後處理*。

1. 停用Day CQ Tagging Service中的Enable validation (`validation.enabled`)屬性。

1. 請確定`com.adobe.fmdita.config.ConfigManager`中的`uuid.regex`屬性資料夾已正確設定。 如果空白，請將其設定為預設值 — `^GUID-(?<id>.*)`。
1. 為`com.adobe.fmdita.uuid`新增個別的記錄器瀏覽器回應也可在`/content/uuid-upgrade/logs`取得。

### 步驟2：執行移轉並驗證

#### 安裝移轉套件

1. 啟動`http://<server-name>/libs/fmdita/clientlibs/xmleditor_uuid_upgrade/page.html`。

   ![移轉中的系統升級索引標籤](assets/migration-system-upgrade.png){width="800" align="left"}

1. 從左側面板選取&#x200B;**系統升級**&#x200B;以執行移轉。 先從資料夾中較小的資料開始，再於`/content/dam`上執行。

1. 在移轉執行時選取[下載報表] **，檢查資料夾中的所有檔案是否已正確升級，以及所有功能是否只適用於該資料夾。**


>[!NOTE]
>
> 內容移轉可在資料夾層級、完整`/content/dam`或相同資料夾上執行（重新執行移轉）。

此外，請務必確實針對所有媒體資產完成內容移轉，例如您在DITA內容中使用的影像和圖形。

#### 基準線及檢閱移轉

從左側面板選取&#x200B;**基準線/檢閱升級**，以移轉基準線並在資料夾層級檢閱。

![移轉中的基準與檢閱索引標籤](assets/migration-baseline-review-upgrade.png){width="800" align="left"}


### 步驟3：還原設定

成功移轉伺服器後，請啟用後處理、標籤和下列工作流程（包括移轉期間最初停用的所有其他工作流程）以繼續在伺服器上運作。

* DAM更新資產工作流程
* DAM中繼資料工作流程

>[!NOTE]
>
>如果某些檔案在移轉前未處理或損毀，則會在移轉前損毀，甚至在移轉後仍會損毀。

## 移轉驗證

1. 移轉完成後，請從左側面板選取&#x200B;**驗證系統升級**，並在移轉前後驗證輸出檔案，以確保移轉成功。

   ![在移轉中驗證系統升級索引標籤](assets/migration-validate-system-upgrade.png){width="800" align="left"}


1. 完成驗證後，可執行壓縮以回收大部分的磁碟空間（請參閱`https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=en`）。
