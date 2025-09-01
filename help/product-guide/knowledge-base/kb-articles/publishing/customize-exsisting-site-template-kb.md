---
title: 為AEM Guides自訂現有的AEM網站範本
description: 瞭解如何為AEM Guides自訂現有的AEM網站範本
feature: Installation
role: Admin
level: Experienced
source-git-commit: 1cec8975e8aad56184793a023d066aa467d8cec5
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 1%

---

# 為AEM Guides自訂現有的AEM網站範本

本指南提供逐步指示，讓您自訂現有的AEM網站範本，以便與AEM Guides搭配使用，從DITA map和主題產生AEM Sites。

如果您使用現成可用的AEM Guides (AEMG Docs)範本，設定和元件已準備就緒，可按原樣使用以發佈您的AEM Guides內容。 不過，如果您想要搭配自訂品牌使用現有的AEM Sites範本來發佈AEM Guides內容，請依照下列步驟，將您的網站範本與AEM Guides演算需求保持一致。


## 先決條件

- 您擁有AEM範本的適當許可權和存取權。
- 您瞭解AEM可編輯範本和AEM網站結構。
- 您已有使用可編輯範本建立的現有網站階層。
- 您現有專案中至少有兩個範本：

   - **檔案容器頁面範本**&#x200B;用於將DITA map呈現為檔案根。
   - **主題頁面範本**&#x200B;用於呈現個別DITA主題頁面。

## 範本命名考量事項

範本名稱會依專案設定而有所不同。 例如，在OOTB AEMG Docs設定中：

- 檔案容器頁面： /conf/AEMG-Docs-Site/settings/wcm/templates/kb-content

- 主題頁面： /conf/AEMG-Docs-Site/settings/wcm/templates/topic-content

**自訂：**&#x200B;自訂程式包含兩個主要步驟：

1. 範本設定：識別並設定兩個範本（容器和主題）。
2. 轉譯指南元件：內嵌必要的AEM Guides元件，以啟用目錄、導覽和中繼資料顯示等功能。

## 範本設定

從您的AEM網站選擇並設定兩個可編輯的範本。

### 檔案容器頁面範本

「檔案容器頁面」範本是用來建立轉譯DITA map內容的「產品檔案容器」頁面。

- 它是特定檔案集（例如產品手冊或指南）的入口點或首頁。
- 將id=&quot;category-page&quot;屬性新增至範本之初始節點的jcr:content。 這可確保AEM Guides會自動將從此範本建立的所有頁面視為檔案容器。

  ![正在新增ID=&quot;category-page&quot;](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-id-category-page.png){width="650" align="left"}

- 新增具有強制屬性的文字元件： text=&quot;$category.html$&quot;。

  ![正在新增文字元件](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-text-component.png){width="650" align="left"}

- 通常會包含導覽元素，例如檔案內章節或主題的連結。
- 它可以自訂為包含品牌、頁首、頁尾和其他設計元素。

**範例使用案例：**
如果您有產品手冊的DITA map，檔案容器頁面範本將會產生該手冊的首頁，顯示概覽和個別主題的連結。

### 主題頁面範本

- **主題頁面範本**&#x200B;用於建立個別&#x200B;**DITA主題**&#x200B;的頁面。
- DITA map中的每個主題都會使用此範本呈現為個別頁面。
- 包含具有必要屬性的&#x200B;**文字元件**： text=&quot;$topic.content$&quot;。

  ![正在新增具有必要屬性的文字元件](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-text-component-mandatory-property.png){width="650" align="left"}

- 在網站產生期間，此預留位置會取代為DITA主題的實際內容。
   - 文字元件通常置於&#x200B;**Container元件**&#x200B;內，以確保配置與樣式正確無誤。
   - 可以自訂以包含所有主題頁面一致的頁首、頁尾和導覽元素。

**範例使用案例：**
如果您有有關「安裝指示」的DITA主題，主題頁面範本將會產生顯示該主題內容的頁面。

**容器元件：**

![正在新增容器元件](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-container-component.png){width="650" align="left"}

>[!NOTE]
>
> 請確定wcm/foundation/components底下使用sling:resourceType的元件已移轉至對應的核心/wcm/components。

在相同範本的結構中新增相同的（容器和文字元件）：

![正在新增容器和文字元件](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-container-and-text-component.png){width="650" align="left"}

## 自訂範本中的轉譯指南元件

若要啟用目錄、頁面重新導向、導覽和中繼資料顯示等核心AEM Guides元件功能，您必須在自訂範本中加入特定AEM Guides元件。 這些元件必須明確新增至對應的可編輯範本（檔案容器頁面或主題頁面），以確保目標功能在網站產生和執行階段期間可用。

如需元件及其使用方式的清單，請參閱下表：

| 功能 | 元件名稱 | 說明 | 建議的範本 |
|---|---|---|---|
| 目錄 | guidessidenavigation | 從DITA map轉譯完整的TOC | 檔案容器 |
| 頁面重新導向 | childredirect | 重新導向地圖中的第一個主題頁面 | 檔案容器 |
| 迷你目錄 | minitoc | 顯示目前主題的目錄 | 主題頁面 |
| 最近更新 | pageproperty | 顯示上次修改日期 | 主題頁面 |
| 傳呼機 | 傳呼機 | 允許在上一個和下一個主題頁面之間導覽 | 主題頁面 |
| 語言導覽 | languagenavigation | 啟用不同語言版本之間的切換 | 任一範本 |


## 元件使用案例

- **重新導向元件(childredirect)：**&#x200B;將此元件新增至檔案容器頁面範本，讓從DITA map產生的產品首頁自動重新導向至第一個主題頁面。 如果您的檔案容器頁面設計為具有自訂元件和配置的獨立首頁，則不需要此元件。

- **目錄(guidessidenavigation)：**&#x200B;將此專案新增至主題頁面範本，以便與主題內容一起呈現可瀏覽的目錄。 TOC衍生自DITA map，可協助使用者瀏覽同層級主題。


## 啟用Guides使用者端程式庫

依預設，AEM Guides元件套件中提供的使用者端資料庫(clientlibs)不會套用至自訂範本。 若要啟用這些功能：

1. **編輯範本：**

   1. 以&#x200B;**編輯器模式**&#x200B;開啟&#x200B;**產品頁面**。
   2. 選取&#x200B;**編輯範本** (這將開啟conf/settings/wcm/templates/structure.html之類的URL)。

      ![編輯範本](/help/product-guide/knowledge-base/kb-articles/assets/publishing/edit-template.png){width="650" align="left"}

2. **更新頁面原則：**

   1. 移至&#x200B;**頁面資訊**&#x200B;按鈕，並選取&#x200B;**頁面原則**。
   2. 新增下列使用者端程式庫：
      - **使用者端資料庫**
      - **使用者端資料庫JavaScript頁面標題**

3. **儲存變更：**&#x200B;新增必要的使用者端程式庫後儲存範本。

   ![新增使用者端資料庫](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-client-libraries.png){width="650" align="left"}


>[!NOTE]
>
> 請務必先在非生產環境中測試範本，然後再部署到生產環境。<br><br>如需詳細資訊，請參閱正式[AEM Guides](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-guides/using/overview)和[AEM Sites](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-core-components/using/get-started/authoring)檔案。
