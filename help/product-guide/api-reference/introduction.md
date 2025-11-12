---
title: 簡介
description: AEM Guides API參考指南簡介
exl-id: d8ee9cf7-1d67-4b4a-aa80-64e893a99463
feature: API Introduction
role: Developer
level: Experienced
source-git-commit: 67e844faece8b6bb8988bb0e67f357cda1db9a4d
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# 簡介 {#id1761C0007W7}

Adobe Experience Manager Guides \(後來稱為&#x200B;*AEM Guides*\)是端對端的企業解決方案，可讓Adobe Experience Manager \(AEM\)擁有元件內容管理解決方案\(CCMS\)功能，以建立及傳遞DITA式內容。 客戶可以使用AEM Guides API以程式設計方式存取AEM Guides工作流程，以便將其與其他企業應用程式整合。 Adobe合作夥伴也可以使用這些API，透過擴充其功能或將其與其他應用程式或服務整合來增強AEM Guides的價值主張。

## AEM GUIDES API

AEM Guides API有兩種格式：

- [Java型API](#java-based-apis)
- [REST型API](#rest-based-apis)

這些API向應用程式開發人員公開AEM Guides的主要功能。 使用這些函式，開發人員可以建立自己的外掛程式，以擴充現成的工作流程。 API可用於管理DITA內容的輸出、使用DITA map、將條件屬性加入資料夾層級設定檔，以及將HTML和Words檔案轉換為DITA格式。


### Java型API

您可以使用Experience Manager Guides中提供的Java式API來建立自訂外掛程式，並擴充現成可用的工作流程。

**從AEM Guides as a Cloud Service的Maven中央存放庫設定SDK**

>[!INFO]
>
>檢視[![javadoc](https://javadoc.io/badge2/com.adobe.aem/aem-dox-sdk-api/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem/aem-dox-sdk-api/latest/index.html)，以取得有關使用Experience Manager Guides as a Cloud Service的Java式API的最新和詳細檔案。

若要在專案中設定和使用Maven存放庫中的服務API JAR，請在專案的`pom.xml`檔案中新增API SDK作為專案相依性，如下所示。

    ``XML
    &lt;相依性>
    &lt;groupId>com.adobe.aem&lt;/groupId>
    &lt;artifactId>aem-dox-sdk-api&lt;/artifactId>
    &lt;version>${RELEASE}&lt;/version>
    &lt;/dependency>
    
    `&#39;

>[!NOTE]
>
> 確保您使用與伺服器上安裝的AEM Guides套件相同版本的API JAR。

**從Maven中央存放庫（內部部署）設定及使用API JAR**

>[!INFO]
>
>檢視[![javadoc](https://javadoc.io/badge2/com.adobe.aem/aem-guides-sdk-api/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api/latest/index.html)，以取得有關使用適用於Experience Manager Guides內部部署設定的Java式API的最新和詳細檔案。

若要針對內部部署設定和使用服務API JAR，請在專案的`pom.xml`檔案中新增服務API JAR做為專案相依性，如下所示：

    ``XML
    &lt;相依性>
    &lt;groupId>com.adobe.aem&lt;/groupId>
    &lt;artifactId>aem-guides-sdk-api&lt;/artifactId>
    &lt;version>${RELEASE}&lt;/version>
    &lt;/dependency>
    
    `&#39;

>[!NOTE]
>
> 確保您使用與伺服器上安裝的AEM Guides套件相同版本的API JAR。


**從AEM Guides公用Maven存放庫設定及使用API JAR （內部部署）**

>[!NOTE]
>
> 公用的AEM Guides Maven存放庫將在Experience Manager Guides 5.3.0版發行後淘汰。 此API JAR此後將只能在Maven中央存放庫中使用。

執行以下步驟，使用公共Maven存放庫中的服務API JAR：

1. 在您的`pom.xml`或`settings.xml`檔案中設定AEM Guides公用Maven存放庫，如下所示：

   ```XML
   <repository>
       <id>fmdita-public</id>
       <name>fmdita-public</name>
       <url>https://repo.aem-guides.com/repository/fmdita-public</url>
    </repository>
   ```

1. 設定存放庫後，將服務API JAR新增為專案`pom.xml`檔案中的專案相依性。

   ```XML
   <dependency>
       <groupId>com.adobe.fmdita</groupId>
       <artifactId>api</artifactId>
       <version>${RELEASE}</version>
   </dependency>
   ```

   >[!NOTE]
   >
   > 使用與您在伺服器上安裝的AEM Guides套件相同版本的API JAR。

一旦在專案的`pom.xml`檔案中將服務API JAR新增為專案相依性，您就可以在專案中建置和使用AEM Guides Java API。


### REST型API

Experience Manager Guides提供了一組完整的REST型API，讓開發人員可透過HTTP存取核心功能並與之互動。

這些API非常適合：

- 將Experience Manager Guides與其他企業系統整合
- 自動化發佈和稽核工作流程
- 建置自訂應用程式和擴充功能

如需API使用、引數和範例要求的詳細資訊，請檢視Experience Manager Guides檔案&#x200B;**API參考**&#x200B;章節中的相關主題。

## 其他資源

以下是AEM Guides其他實用資源的清單，這些資源可在[學習與支援](https://helpx.adobe.com/support/xml-documentation-for-experience-manager.html)頁面上取得：

- 使用手冊
- 安裝及設定指南
- 快速入門手冊
- [說明封存頁面](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html) \（存取舊版檔案\）
