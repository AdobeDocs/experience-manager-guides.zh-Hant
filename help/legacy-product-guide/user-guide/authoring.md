---
title: 管理內容
description: 在AEM Guides中管理內容並識別您的角色和許可權。 瞭解內容管理以及使用全域或檔案夾層級設定檔的主要概念。
feature: Content Management
role: User
hide: true
exl-id: 54b960cf-fb00-4d4a-a836-9de4738c49a8
source-git-commit: 7286c3fb36695caa08157296fd6e0de722078c2b
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 9%

---

# 管理內容 {#id164JBG0M0T1}

開始實際建立內容之前，您必須先熟悉AEM Guides中內容管理的一些基本概念。 然後，從建立不同的使用者群組並組織您的資產開始。

## 重要概念

AEM中內容管理的一些主要概念如下：

**資產管理**

AEM Guides使用AEM的數位資產管理\(DAM\)來管理您的DITA檔案。 您上傳或簽入DAM的檔案會儲存為數位資產。 您可以在AEM Assets中管理和編輯資產。 如需資產管理的詳細資訊，請參閱[管理資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/manage-digital-assets.html?lang=zh-Hant)。

**連結管理**

移動或重新命名檔案，或變更內容存放庫中的資料夾結構，不必擔心參照損毀。 受影響的內容的所有參考資料都會自動更新。 刪除從其他位置參照的內容時，系統會顯示警告訊息，以防止無意間中斷。

**管理版本**

AEM Guides為您的數位資產提供版本管理。 您可以輕鬆地從所選擇的DITA編寫應用程式啟用此功能。 允許編寫者執行標準版本控制功能，例如簽入和簽出。

如需建立版本或還原至特定版本的詳細資訊，請參閱[分支、還原及後續版本設定](web-editor-preview-topics.md#id193PG0Y051X)。

**原生DITA處理**

雖然AEM Guides可維護DITA檔案的結構，但同時也讓AEM能夠使用元素對應，將DITA元素對應至AEM元件，以原生方式處理DITA。 原生DITA處理用於主題預覽、AEM Sites發佈和稽核工作流程等功能。

## 識別您的角色和許可權 {#id181TF0K0MHT}

AEM Guides提供三個現成可用的群組。 這些群組是： *作者*、*檢閱者*&#x200B;和&#x200B;*發佈者*。 根據您關聯的群組，您有權執行下表中提及的特定工作。 例如，發佈工作只能由發佈者執行，不能由作者或稽核者執行。 同樣地，作者可以建立新主題，而稽核者只能稽核主題。

>[!TIP]
>
> 如需設定使用者許可權的最佳實務，請參閱「最佳實作指南」中的&#x200B;*許可權*&#x200B;區段。

下表列出各種工作以及可執行這些工作的群組：

| 任務 | 作者 | 檢閱者 | 發佈者 |
|----|-------|---------|----------|
| 建立DITA主題 | 是 |   | 是 |
| 建立DITA Map | 是 |   | 是 |
| 對應集合 | 是 |   | 是 |
| 建立評論任務 | 是 |   | 是 |
| 檢閱主題[1](#fntarg_1) | 是 | 是 | 是 |
| 關鍵解析度 | 是 |   | 是 |
| 簽出/簽入 | 是 |   | 是 |
| 編輯主題 | 是 |   | 是 |
| 移動主題 | 是 |   | 是 |
| 編輯主題屬性 | 是 |   | 是 |
| 複製 | 是 |   | 是 |
| 刪除 | 是 |   | 是 |
| 共用 | 是 |   | 是 |
| **檔案狀態** |
| 建立/編輯檔案狀態設定檔 |   |   | 是 |
| 變更檔案狀態[2](#fntarg_2) | 是 | 是 | 是 |
| **DITA map主控台中可用的功能\（輸出預設集索引標籤\）** |
| 產生 |   |   | 是 |
| 編輯 |   |   | 是 |
| 重複項目 |   |   | 是 |
| 建立 |   |   | 是 |
| 刪除預設集 |   |   | 是 |
| **DITA map主控台中可用的功能\（輸出標籤\）** |
| 檢視產生的輸出 | 是 |   | 是 |
| **DITA map主控台中可用的功能\（主題標籤\）** |
| 建立評論任務 | 是 |   | 是 |
| 編輯 | 是 |   | 是 |
| **DITA map主控台中可用的功能\（基準線標籤\）** |
| 建立 |   |   | 是 |
| 編輯 |   |   | 是 |
| 重複項目 |   |   | 是 |
| 移除 |   |   | 是 |
| DITA map主控台\（報表標籤\） | 是 |   | 是 |
| DITA map主控台中可用的&#x200B;**功能\（條件預設集\）** |
| 建立/編輯條件預設集 |   |   | 是 |

[1](#fnsrc_1)如果邀請&#x200B;*作者*&#x200B;與&#x200B;*發行者*&#x200B;檢閱。

[2](#fnsrc_2)根據檔案狀態設定檔中授予使用者的許可權。

## 內容製作的先決條件

**使用全域或資料夾層級的設定檔**

在企業中，不同的群組或產品可能會使用不同的編寫範本、輸出範本、條件屬性設定檔\（或主旨配置\）和網頁編輯器設定。 僅在企業層級\（或全域\）設定這些專案，可能會讓作者體驗困難，因為他們會看到與他們無關的範本或設定檔。

AEM Guides可讓您在企業\（全域\）層級和檔案夾層級設定編寫\（主題或地圖\）範本、輸出範本、條件屬性和Web編輯器設定。 如此一來，您就可以分隔企業中不同部門或產品的組態。

此外，您也可以將檔案夾特定的設定委派給部門或產品管理員，以分散管理。

如需設定全域和資料夾層級設定檔的詳細資訊，請參閱安裝和設定Adobe Experience Manager Guides as a Cloud Service中的&#x200B;*設定全域或資料夾層級設定檔*。
