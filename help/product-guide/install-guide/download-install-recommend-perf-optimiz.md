---
title: Recommendations的效能最佳化
description: 瞭解效能最佳化的Recommendations
exl-id: b2a836a0-de82-4d89-aae3-43276997da74
feature: Performance Optimization
role: Admin
level: Experienced
source-git-commit: b28b7d96cce69f677b0bcf891b94d7ac84eb1eb0
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---

# Recommendations的效能最佳化 {#id213BD0JG0XA}

## 設定資料存放區\（必要\）

**有什麼變更？**
在設定`org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.`下將`minRecordLength`屬性設定為值`100`如需檔案日期存放區和S3資料存放區的詳細資訊，請參閱[在AEM 6](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/data-store-config.html)文章中設定節點存放區和資料存放區。

>[!NOTE]
>
> 對於S3資料存放區，維護資料存放區中內容的成本也取決於請求數量。 因此，在使用S3進行此設定時，也應考量每個請求的設定成本和快取大小。

**何時設定？**
初始設定之後，但在任何內容移轉之前。 您即使是在現有系統上也必須執行此變更，以確保所有新內容都儲存在資料存放區而非區段存放區中。

**此變更的結果**
DITA檔案儲存在資料存放區中，而非區段存放區中。 這會將區段存放區大小保持在建議的限制之下，進而改善系統的回應能力。

## 更新Lucene索引\（強制\）

**有什麼變更？**
從oak：index/lucene排除/var/dxml。

>[!NOTE]
>
> AEM Guides從未使用Lucene索引來搜尋/var/dxml節點中的內容。

**何時設定？**
如果您在移轉內容之前在新系統上進行了此變更，則只需更新oak：index/lucene。 否則，在內容已移轉的現有系統上，然後在oak：index/lucene中進行變更後，重新建置Lucene \(*)的索引，可能需要數小時才能完成*\)。

**此變更的結果**
此變更會防止/var/dxml節點編制索引並儲存在區段存放區中。

## Java記憶體最佳化\（必要\）

**有什麼變更？**
JVM啟動引數應根據基礎架構和磁碟大小仔細調整。 建議您洽詢Adobe支援，取得存取理想設定的協助。 不過，您可以自行嘗試下列設定：

 — 將JVM棧積大小設定為最小總可用記憶體的1/4。 使用引數`-Xmx<size>`設定棧積記憶體大小。 設定 — `Xms`的值等於`-Xmx`。

 — 啟用`-XX:+HeapDumpOnOutOfMemoryError`並設定`-XX:HeapDumpPath=</path/to/folder` `>`的路徑。

 — 啟用Java GC記錄為：

`* -XX:+PrintGCDateStamps`

`* -verbose:gc`

`* -XX:+PrintGCDetails`

`* -XX:+PrintTenuringDistribution`

`* -Xloggc:</path/to/gc.log>`

 — 一般而言，對於Java 11，使用G1GC \(`-XX:+UseG1GC`\)；對於Java 8，使用CMS \(-`XX:+UseConcMarkSweepGC`\)。

 — 使用`-XX:NewRatio`控制新世代記憶體大小的大小。 預設值為2，這表示有1/3的記憶體用於年輕一代。 由於有許多物件會快速建立並銷毀，使用值1會將記憶體的1/2配置給年輕一代。

 — 使用`-XX:MaxTenuringThreshold`控制要升級至舊世代的物件數目。 使用值15 \（預設\）可延遲將物件升級至舊世代的時間。

**何時設定？**
如果您要在現有系統上進行此變更，則需要重新啟動系統。 若是全新安裝，此變更應在系統啟動前於啟動指令碼\(.bat或.sh\)檔案中進行。

**此變更的結果**
這會產生最佳棧積大小並規範GC的執行。

## 製作例項上的使用者端資料庫縮制\（選用\）

**有什麼變更？**
使用者端資料庫應在編寫執行個體中設定為最小化。 這可確保在使用者從不同位置瀏覽系統時，要下載的位元組會更少。 若要進行此變更，請從Felix主控台在&#x200B;**HTML程式庫管理員**&#x200B;中設定組態。

**何時設定？**
您可以透過Felix主控台或程式碼部署，在執行階段完成此操作。

**此變更的結果**
這項變更可改善編寫執行個體上頁面的載入時間，因為用來載入使用者端程式庫的傳輸位元組減少。

## 設定同時發佈的執行緒\（必要，視使用案例而定\）

**有什麼變更？**
如果您使用DITA-OT來發佈輸出，且已定義多個並行發佈執行緒，則需要此變更。

根據預設，AEM Guides會將發佈執行緒設定為CPU+1數量。 不過，建議將此值設定為CPU總數的一半\(1/2\)或三分之一\(1/3\)。 若要這麼做，請根據建議在設定`com.adobe.fmdita.publish.manager.PublishThreadManagerImpl`下設定&#x200B;**產生集區大小**&#x200B;屬性。

**何時設定？**
您可以透過Felix主控台或程式碼部署，在執行階段完成此操作。

**此變更的結果**
此變更可確保在執行中的作者執行個體上，所有資源都不會配置給發佈作業。 這樣可讓作者也能使用系統資源，進而提供更佳的使用者體驗。

## 設定AEM Site輸出產生的節點批次大小\（必要，視使用案例而定\）

**變更內容？**
如果您產生AEM Sites輸出，則必須進行此變更。

根據您的系統組態，將`com.adobe.fmdita.config.ConfigManager`下棧積&#x200B;**屬性中的** Limit AEM Site Pages設為數字。 此屬性會定義產生網站頁面時要認可的節點批次大小。 例如，在具有較大數量CPU和棧積大小的系統上，您可以將預設值從`500`增加到較大的數量。 您必須使用變更的值來測試回合，才能達到此屬性的最佳值。

**何時設定？**
您可以透過Felix主控台或程式碼部署，在執行階段完成此操作。

**此變更的結果**
棧積&#x200B;**屬性中** Limit AEM Site Pages的增加數目會最佳化AEM Site輸出產生程式。


**上層主題：**&#x200B;[&#x200B;下載並安裝](download-install.md)
