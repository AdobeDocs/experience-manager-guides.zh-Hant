---
title: 設定資料來源的自訂聯結器
description: 瞭解如何設定資料來源的自訂聯結器。
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: fdd19363c6768860ffa2f70c934b6f71c811c08b
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 0%

---

# 設定自訂資料來源聯結器

Experience Manager Guides可讓您根據自己的需求自訂聯結器，然後將其用於不同的資料來源。 若要自訂聯結器，您必須實作聯結器介面及其重要功能，然後設定介面。 您也可以提供資源以及自訂聯結器。


- [自訂Experience Manager Guides的聯結器](#customize-connector)
- [實作聯結器介面](#implement-interface)
- [重要函式](#important-functions)
- [預設聯結器實作的型別](#default-connectors)
   - [設定介面](#config-interface)
   - [預設設定實作的型別](#default-config-types)
   - [具體設定實施](#concrete-config-implementation)
   - [其他資源](#resources)



## 自訂Experience Manager Guides的聯結器 {#customize-connector}

您可以使用預先定義的介面和抽象類別，自訂或設定資料來源的聯結器。 您可以在[https://github.com/adobe/guides-data-source-connectors/tree/main/konnect-definitions](https://github.com/adobe/guides-data-source-connectors/tree/main/konnect-definitions)取得完整的原始程式碼。


有關konnect定義，請參閱[![javadoc](https://javadoc.io/badge2/com.adobe.aem.addon.guides/konnect-definitions/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem.addon.guides/konnect-definitions)。

## 實作聯結器介面 {#implement-interface}

根據您的需求，執行以下步驟來實作介面及其功能：

1. 為聯結器定義與系統整合的標準化方式，以允許執行查詢、驗證連線和擷取中繼資料。
1. 提供設定範本、標誌、查詢和其他設定的預設方法，促進UI整合。
1. 請確定聯結器已正確驗證，並且在與資料來源互動時可以處理錯誤(`KonnectException`)。

此介面可做為實作各種資料聯結器型別的藍圖，確保聯結器符合大型軟體生態系統內的任何特定整合和營運需求。

## 重要函式 {#important-functions}

實作下列重要函式：

| 方法 | 必要 | 說明 |
|---|---|---|
| getLogoUrl |  | <ul><li> 此方法會傳回用作聯結器標誌的URL。 <li> 依預設，它會傳回空字串，指出除非覆寫，否則不會提供標誌URL。 <br><b>其他附註</b>： <br> <ul><li> 如果您同時提供標誌URL和標誌類別名稱，則標誌URL會用來在使用者介面中顯示標誌。 <li> 如果您透過組態設定來指定標誌URL，它會覆寫在方法實作中設定的URL。 |
| validateConnection | 是 | <ul><li> 使用此方法來驗證聯結器是否可以建立與其資料來源的連線。 <li> 它以`ConfigDto`物件作為引數，其中包含組態設定，例如連線認證和端點URL。 <li> 如果驗證（連線測試）成功，則方法會傳回true，表示聯結器可以連線至其資料來源。 |
| 執行 | 是 | <ul><li>使用此方法執行聯結器的單一查詢，並與資料來源互動。 <li> 支援此操作的聯結器會處理查詢執行、剖析回應，並視需要將其轉換為JSON字串。 <li> 在`QueryInfoDto`物件中封裝要在此方法中執行的查詢，其中包含查詢字串和引數等詳細資訊。 <li> 方法會傳回JSON字串，代表執行查詢的回應。 <br><b>個其他附註</b>： <li>此方法的實作會因特定聯結器及其與資料來源的互動而異。 <li> 使用`KonnectException`處理在執行或連線至資料來源期間發生的任何例外狀況或錯誤。 |
| executeWithLimit | 是 | <ul><li> 使用此方法的目的與`execute()`相同，但具有套用限制查詢的附加功能，通常用於顯示UI元件中的預覽。 <li> 支援此操作的聯結器會處理查詢執行、剖析回應，並視需要將其轉換為JSON字串。 <li> 在`QueryInfoDto`物件中封裝要在此方法中執行的查詢，類似於上一個方法。 <br><b>個其他附註</b>： <ul><li> `QueryResultDto`是封裝查詢執行結果（包括有關查詢及其執行狀態的中繼資料）的自訂類別或資料傳輸物件。 |
| getsamplequery | | <ul><li>此方法會傳回範例查詢字串，該字串會顯示在UI中（例如使用者可插入或編輯查詢的對話方塊）中。 <li>依預設，它會傳回空字串，表示除非覆寫，否則不會提供範例查詢。 <br><b>個其他附註</b>： <ul> <li> 如果您未定義範例查詢，而方法傳回空字串，則UI插入查詢對話方塊中不會顯示範例查詢。 |
| getTemplates | | <ul> <li> 此方法會傳回與聯結器關聯的範本清單。 <li> 依預設，它會傳回空白清單，指出除非覆寫，否則不會提供任何範本。 |
| getlogoclassname | | <ul> <li> 此方法會傳回類別名稱做為聯結器的標誌。 依預設，它會傳回空字串，表示除非覆寫，否則不會提供標誌類別名稱。 <br><b>個其他附註</b>： <ul><li> 如果您同時提供標誌URL和標誌類別名稱，則標誌URL會用來在使用者介面中顯示標誌。 <li> 如果您透過組態設定來指定標誌類別名稱，它會覆寫在方法實作中設定的類別名稱。 |
| 已啟用 | 是 | <ul><li> 此方法會檢查是否已啟用`connector`。 <li> 依預設，方法會傳回false，表示除非實作此方法的類別覆寫，否則不會啟用聯結器。 |
| getDescription | | <ul><li>使用此方法可傳回可在UI中顯示的說明字串。 <li> 依預設，它會傳回空字串，表示除非覆寫，否則不會提供任何說明。 |
| getAuthor | | <ul><li> 此方法可讓您擷取建立或負責聯結器的作者名稱。 <li> 它通常有助於識別並認可系統或框架中的聯結器建立者或維護者。 |
| getName | 是 | <ul><li>此方法可讓您擷取指派給聯結器的唯一名稱。 <li>傳回的名稱對於在使用者介面(UI)內容中識別聯結器至關重要，尤其是如果聯結器的組態設定未明確指定名稱。 <li>此名稱用於各種UI元件中，好記的方式顯示或管理聯結器。 |
| getGroup | 是 | <ul> <li>此方法可讓您擷取與聯結器關聯的群組名稱。 <li>群組名稱通常用於根據聯結器的功能、用途或型別將聯結器組織或分類為邏輯群組。 <li> 如此可讓您在設定UI中更輕鬆地管理和呈現聯結器。 |
| getDefaultTemplatePath |  | <ul><li> 此方法會傳回與此聯結器關聯的範本預設路徑。 <li> 依預設，它會傳回空字串，指出除非覆寫，否則不會設定預設路徑。 |
| getLogoSv |  | <ul><li>使用此方法可傳回聯結器標誌的SVG表示法。 <li> 依預設，它會傳回空字串，表示除非覆寫，否則不會提供任何SVG資料。 |
| getMaxNoRowsForPreviewQuery | | <ul><li>此方法會傳回UI預覽中查詢或顯示的最大列數。 <li> 依預設，它會傳回DEFAULT_LIMIT_PREVIEW的值，此常數代表預覽列的預設限制。 |
| getconfigclass | 是 | <ul><li>此方法提供有關實作Config介面且受此聯結器支援的類別的資訊。 <li> 它可讓應用程式或架構動態地探索及使用與聯結器相容的設定。 |

## 預設聯結器實作的型別 {#default-connectors}

*konnect-definitions*&#x200B;資料庫提供抽象聯結器實作，並具有預先定義的函式以執行查詢。 這些聯結器實作可作為範本，直接擴充並按原樣使用。 如果需要自訂實施，則可覆寫其函式。

除了實作預設聯結器之外，您也可以實作下列其中一個預設抽象類別：

- Rest聯結器
- 檔案聯結器
- GraphQL聯結器
- SQL聯結器
- NoSQL聯結器


如果聯結器符合其中一種型別，請將聯結器延伸至對應的基底類別。 否則，請實作聯結器介面從頭開始建立。

## 設定介面 {#config-interface}

`Config`介面設計用來設定具有特定驗證方法的資料來源，讓您精確控制連線的建立方式。

`Config`介面提供處理及實作驗證詳細資料方式的彈性。 不同的實作可提供多種驗證資料來源的方式。 聯結器使用Config執行個體對資料來源執行及驗證查詢，以形成完整的工作流程。
聯結器使用`Config`執行個體對資料來源執行及驗證查詢，以形成完整的工作流程。

設定實作會定義如何處理驗證以連線至資料來源。 然後，聯結器實作會使用此設定來與資料來源互動，確保查詢可正確執行和驗證。

整體而言，`Config`介面是連線至資料來源的工作流程中重要的一環，尤其著重於驗證設定。

### 預設設定實作的型別 {#default-config-types}

驗證有三種型別的預設抽象設定實作：

- RestConfig
- SqlConfig
- NoSqlConfig

如果設定符合其中一個型別，則可以擴充對應的基底類別。 否則，可透過實作Config介面從頭開始建立。

### 具體設定實施 {#concrete-config-implementation}

*konnect-definitions*&#x200B;資料庫隨附預先定義的Config介面實作，以供某些廣泛使用的驗證設定使用。 您可以直接在聯結器中使用這些設定，或使用「設定」介面定義新設定。 這些實施包括：

- API金鑰驗證設定
- 基本驗證權杖型設定
- 基本驗證設定
- 持有人權杖設定
- SQL的使用者名稱密碼設定
- NoSQL的連線字串驗證設定

### 其他資源{#resources}

Experience Manager Guides也可讓您為圖志和範本以及實作提供自訂資源。 您可以將這些資源保留在`resources`資料夾中。
若要讓聯結器可使用這些功能，您必須實作下列聯結器功能：


- `getLogoSvg` — 以字串傳回標誌SVG。

- `getTemplates` — 傳回指定格式的範本清單。