---
title: 簡介
description: AEM Guides API參考指南簡介
exl-id: d8ee9cf7-1d67-4b4a-aa80-64e893a99463
feature: API Introduction
role: Developer
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---

# 簡介 {#id1761C0007W7}

Adobe Experience Manager Guides \(後來稱為&#x200B;*AEM Guides*\)是端對端的企業解決方案，可讓Adobe Experience Manager \(AEM\)擁有元件內容管理解決方案\(CCMS\)功能，以建立及傳遞DITA式內容。 客戶可以使用AEM Guides API以程式設計方式存取AEM Guides工作流程，以便將其與其他企業應用程式整合。 Adobe合作夥伴也可以使用這些API，透過擴充其功能或將其與其他應用程式或服務整合來增強AEM Guides的價值主張。

## AEM GUIDES API

AEM Guides API有兩種格式：HTTP和Java。 這些API向應用程式開發人員公開AEM Guides的主要功能。 使用這些函式，開發人員可以建立自己的外掛程式，以擴充現成的工作流程。 API可用於管理DITA內容的輸出、使用DITA map、將條件屬性加入資料夾層級設定檔，以及將HTML和Words檔案轉換為DITA格式。

## 在本機Apache Maven存放庫中安裝JAR {#install-jar-local}

為了能夠使用AEM Guides公開的JAR檔案，您需要將它們安裝在您的本機Apache Maven存放庫上。 執行以下步驟以在您的位置Maven存放庫中安裝JAR：

1. 在您的本機系統上解壓縮AEM Guides套件\(.zip\)檔案的內容。

2. 在命令提示字元中，導覽至擷取內容路徑中的下列資料夾：

   ```
   \jcr_root\libs\fmdita\osgi-bundles\install
   ```

3. 執行以下命令，將API套件組合安裝至本機Maven存放庫：

   ```
   mvn install:install-file -Dfile=api-X.x.jar -DgroupId=com.adobe.fmdita -DartifactId=api -Dversion=X.x -Dpackaging=jar**
   ```

   >[!NOTE]
   >
   > 在上述命令中，X.x應該以Dfile和Dversion引數中的實際版本編號取代。

4. \（*選擇性*\）在本機Maven專案的存放庫中安裝相依性。 您可以在Maven專案中建立資料夾，然後使用下列其他引數執行上一步驟中指定的`mvn install`命令來達成此目的：

   ```
   -DlocalRepositoryPath=<path_to_project_repository>
   ```

   接下來，若要將專案的本機存放庫資料夾公開給Maven建置程式，請在父pom.xml檔案中新增`repository`元素，如下所示：

   ```XML
   <repositories>
      <repository>
         <id>project-repository</id>
         <url>file://${project.basedir}/repository</url>
      </repository>
   </repositories>
   ```


此程式會將API JAR安裝在本機Maven存放庫中。

## 在Maven專案中使用服務API JAR

在本機Maven存放庫中安裝API JAR後，執行以下步驟以在專案中使用JAR：

1. 將JAR新增到您的程式碼基底，並將其提交到資料夾下的程式碼基底存放庫，例如「dependencies」。 請注意，資料夾名稱取決於您的程式碼基底階層。

2. 依照以下方式設定專案pom.xml檔案：

   父專案的pom.xml檔案：

   >[!IMPORTANT]
   >
   > 在以下程式碼片段中，應將X.x取代為實際版本號碼和API JAR的檔案名稱。 此資訊將與[安裝程式](#install-jar-local)的步驟3中所提供的資訊相同。

   ```XML
   <plugin>
   
       <groupId>org.apache.maven.plugins</groupId>
   
      <artifactId>maven-install-plugin</artifactId>
   
       <version>2.5.2</version>
   
       <configuration>
   
               <groupId>com.adobe.fmdita</groupId>
   
               <artifactId>api</artifactId>
   
               <version>X.x</version>
   
               <file>${basedir}/dependencies/fmdita/api-X.x.jar</file>
   
               <packaging>jar</packaging>
   
               <generatePom>true</generatePom>
   
       </configuration>
   
       <executions>
   
           <execution>
   
               <id>inst_fmdita</id>
   
                   <goals>
   
                       <goal>install-file</goal>
   
                   </goals>
   
                   <phase>clean</phase>
   
           </execution>
   
       </executions>
   </plugin>
   ```

   子模組的pom.xml檔案：

   ```XML
   <plugin>
      <groupId>org.apache.maven.plugins</groupId>
   
      <artifactId>maven-install-plugin</artifactId>
   
      <configuration>
   
         <groupId>com.adobe.fmdita</groupId>
   
         <artifactId>api</artifactId>
   
         <version>3.6</version>
   
         <file>${basedir}/../dependencies/fmdita/api-3.6.jar</file>
   
         <packaging>jar</packaging>
   
         <generatePom>true</generatePom>
   
      </configuration>
   
      <executions>
   
         <execution>
   
            <id>inst_fmdita</id>
   
            <goals>
   
               <goal>install-file</goal>
   
            </goals>
   
            <phase>clean</phase>
   
         </execution>
   
      </executions>
   
   </plugin>
   ```


## 從公共Maven存放庫設定並使用服務API JAR

執行以下步驟，在您的專案中設定和使用公用Maven存放庫中的服務API JAR：

1. 若要在專案中使用服務API JAR，請在pom.xml檔案中設定AEM Guides公用Maven存放庫。
2. 依照以下步驟，在Maven的settings.xml檔案中設定公用Maven存放庫：

   ```XML
   <repository>
      <id>fmdita-public</id>
      <name>fmdita-public</name>
      <url>https://repo.aem-guides.com/repository/fmdita-public</url>
   </repository>
   ```

3. 設定存放庫後，在專案的pom.xml檔案中新增服務API JAR作為專案相依性。

   >[!NOTE]
   >
   > 使用與您在伺服器上安裝的AEM Guides套件相同版本的API JAR。

4. 設定Maven相依性，如下所示：

   ```XML
   <dependency>
      <groupId>com.adobe.fmdita</groupId>
      <artifactId>api</artifactId>
      <version>4.0</version>
   </dependency>
   ```


一旦在專案的pom.xml檔案中將服務API JAR新增為專案相依性，您即可在專案中建立並使用AEM Guides Java API。

## 使用AEM Guides的Maven中央存放庫中的API JARas a Cloud Service

對於AEM Guidesas a Cloud Service，API JAR已部署到Maven Central。 您無需任何設定即可使用API JAR。

>[!NOTE]
>
> 已根據雲端附加元件命名慣例更新API jar的命名慣例。

若要使用API JAR，您必須將相依性新增到專案的pom.xml，如下所示：

```XML
<dependency>
   <groupId>com.adobe.aem</groupId>
   <artifactId>aem-guides-sdk-api</artifactId>
   <version>2022.5</version>
</dependency>
```

>[!NOTE]
>
> 由於API JAR內的套件仍然相同，因此不需要變更程式碼即可在現有雲端專案中使用此API JAR。

## 其他資源

以下是AEM Guides其他實用資源的清單，這些資源可在[學習與支援](https://helpx.adobe.com/support/xml-documentation-for-experience-manager.html)頁面上取得：

- 使用手冊
- 安裝及設定指南
- 快速入門手冊
- [說明封存頁面](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html) \（存取舊版檔案\）
