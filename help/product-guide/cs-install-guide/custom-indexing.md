---
title: 自訂索引部署
description: 瞭解如何自訂索引內容
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 7d2d0c21001cd53244588f6b700db184a73ffa77
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 3%

---

# 部署自訂索引以尋找和取代(Source檢視)功能

## 概觀

本指南提供在Adobe Experience Manager (AEM) as a Cloud Service上部署`guidesAssetLucene‑1‑custom‑1`自訂索引的逐步指示。 雖然「作者」檢視中的標準「尋找和取代」功能可無須此索引運作，但在Source檢視中啟用「尋找和取代」時，尤其需要自訂索引。 「尋找和取代」(Source檢視)不僅可讓您搜尋可見的編寫內容，也可搜尋基礎的XML結構；包括元素、標籤和屬性值。

## 先決條件

繼續進行索引部署之前，請確定您已：

- 已安裝&#x200B;**AEM as a Cloud Service環境** AEM Guides
- **存取專案的程式碼基底** （Git存放庫）
- 具有部署許可權的&#x200B;**Cloud Manager存取權**

## 索引定義

若要啟用尋找和取代(Source檢視)功能，您必須將名為&#x200B;**`guidesAssetLucene-1-custom-1`**&#x200B;的自訂索引部署至AEM Cloud Service環境。

### 索引名稱

```
guidesAssetLucene-1-custom-1
```

### 索引定義(.content.xml)

在專案中建立下列索引定義：

`ui.apps/src/main/content/jcr_root/_oak_index/guidesAssetLucene-1-custom-1/.content.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:dam="http://www.day.com/dam/1.0"
          xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:oak="http://jackrabbit.apache.org/oak/ns/1.0"
          xmlns:rep="internal"
          jcr:mixinTypes="[rep:AccessControllable]"
          jcr:primaryType="oak:QueryIndexDefinition"
          async="[async,nrt]"
          compatVersion="{Long}2"
          evaluatePathRestrictions="{Boolean}true"
          includedPaths="[/content/dam]"
          reindex="{Boolean}false"
          reindexCount="{Long}1"
          seed="{Long}958982603885135223"
          selectionPolicy="tag"
          tags="[ditaSearch]"
          type="lucene">

    <aggregates jcr:primaryType="nt:unstructured">
        <dam:Asset jcr:primaryType="nt:unstructured">
            <include0
                    jcr:primaryType="nt:unstructured"
                    path="jcr:content/renditions/original/jcr:content"
                    relativeNode="{Boolean}true"/>
        </dam:Asset>
    </aggregates>

    <analyzers jcr:primaryType="nt:unstructured">
        <default jcr:primaryType="nt:unstructured">
            <tokenizer
                    jcr:primaryType="nt:unstructured"
                    name="Whitespace"/>
        </default>
    </analyzers>

    <indexRules jcr:primaryType="nt:unstructured">
        <dam:Asset
                jcr:primaryType="nt:unstructured"
                indexNodeName="{Boolean}true">
            <properties jcr:primaryType="nt:unstructured">
                <cqTags
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/metadata/cq:tags"
                        nodeScopeIndex="{Boolean}true"
                        propertyIndex="{Boolean}true"
                        useInSpellcheck="{Boolean}true"
                        useInSuggest="{Boolean}true"/>
                <jcrLastModified
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/jcr:lastModified"
                        ordered="{Boolean}true"
                        propertyIndex="{Boolean}true"
                        type="Date"/>
                <jcrCreated
                        jcr:primaryType="nt:unstructured"
                        name="jcr:created"
                        ordered="{Boolean}true"
                        propertyIndex="{Boolean}true"
                        type="Date"/>
                <guidesParentMaps
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/guidesParentMaps"
                        propertyIndex="{Boolean}true"/>
                <guidesDirectParentMaps
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/guidesDirectParentMaps"
                        propertyIndex="{Boolean}true"/>
                <ditaClass
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/metadata/dita_class"
                        propertyIndex="{Boolean}true"/>
                <nodeNameLowerCase
                        jcr:primaryType="nt:unstructured"
                        function="fn:lower-case(fn:name())"
                        ordered="{Boolean}true"
                        propertyIndex="{Boolean}true"/>
                <cqDriveLock
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/cq:driveLock"
                        propertyIndex="{Boolean}true"
                        ordered="{Boolean}true"/>
                <docState
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/metadata/docstate"
                        propertyIndex="{Boolean}true"
                        ordered="{Boolean}true"/>
                <jcrPath
                        jcr:primaryType="nt:unstructured"
                        function="fn:path()"
                        ordered="{Boolean}true"/>
                <dcTitleLowerCase
                        jcr:primaryType="nt:unstructured"
                        function="fn:lower-case(jcr:first(jcr:content/metadata/@dc:title))"
                        propertyIndex="{Boolean}true"
                        ordered="{Boolean}true"/>
                <dcTitle
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/metadata/dc:title"
                        propertyIndex="{Boolean}true"/>
            </properties>
        </dam:Asset>
    </indexRules>

    <tika jcr:primaryType="nt:unstructured">
        <mimeTypes jcr:primaryType="nt:unstructured">
            <application jcr:primaryType="nt:unstructured">
                <xml
                        jcr:primaryType="nt:unstructured"
                        mappedType="application/dita+xml"/>
            </application>
            <text jcr:primaryType="nt:unstructured">
                <markdown
                        jcr:primaryType="nt:unstructured"
                        mappedType="text/markdown+source"/>
            </text>
        </mimeTypes>
    </tika>
</jcr:root>
```

## 部署步驟

如需將自訂索引部署到AEM as a Cloud Service的詳細指示，請檢視[內容搜尋和索引 — AEM as a Cloud Service](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/operations/indexing)。

### 此索引的重要點

依照部署指南操作時，請針對「尋找和取代」索引使用以下細節：

- **索引名稱**： `guidesAssetLucene-1-custom-1`
- **索引型別**：完全自訂索引（不是OOTB索引的自訂）
- **位置**： `ui.apps/src/main/content/jcr_root/_oak_index/guidesAssetLucene-1-custom-1/.content.xml`
- **需要封裝屬性**：
   - `noIntermediateSaves=true`
   - `allowIndexDefinitions=true`

## 重新索引

當您透過AEM as a Cloud Service的CI/CD管道部署索引時，Cloud Manager會&#x200B;**自動**&#x200B;處理重新索引。

索引通常會自動處理。 但是，如果即使在正確部署和索引過程完成後，舊資料仍然無法搜尋，則應執行一次手動重新索引索引操作。

### 有何期望

- 索引工作將在部署後自動啟動。
- 您可以在Cloud Manager建置頁面上監視進度。
- 編制索引期間，環境仍可完全運作。

## 驗證

部署和索引完成後，請驗證索引是否正常運作。

### 驗證索引部署

在您的開發環境中(如果有CRXDE Lite)：

1. 導覽至 `/oak:index/guidesAssetLucene-1-custom-1`。
2. 驗證具有預期設定的節點是否存在。

### 測試尋找和取代功能

主要驗證是測試功能：

1. 開啟AEM Guides。
2. 導覽至&#x200B;**工具** > **指南** > **在存放庫中尋找和取代**。
3. 設定在DITA或Markdown檔案中搜尋文字。
4. 確認已正確傳回搜尋結果。
5. 在測試檔案上測試取代功能。

## 其他資源

- [AEM as a Cloud Service索引檔案](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/operations/indexing)
- [Apache Jackrabbit Oak Indexing指南](https://jackrabbit.apache.org/oak/docs/query/indexing.html)
- [AEM Guides檔案](https://experienceleague.adobe.com/en/docs/experience-manager-guides)
- [Cloud Manager 文件](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager)
