---
title: 使用自訂DITA-OT與DITA專業化
description: 瞭解如何使用自訂DITA-OT和DITA專業化
exl-id: 4d3e0fc1-b684-44f9-ab0d-411033024019
feature: DITA-OT Configuration
role: Admin
level: Experienced
source-git-commit: 3119ef32a753afac9405af31a241ae508f922ea7
workflow-type: tm+mt
source-wordcount: '1701'
ht-degree: 0%

---

# 使用自訂DITA-OT與DITA專業化 {#id181GAJ0005Z}

DITA Open Toolkit \(DITA-OT\)是一組以Java為基礎的開放原始碼工具，可處理DITA map和主題內容。 AEM Guides可讓您輕鬆匯入及使用自訂DITA-OT外掛程式。 匯入後，AEM Guides可設定為使用自訂DITA-OT外掛程式來產生任何格式的輸出。 在產生輸出時，只要選取DITA-OT選項，AEM Guides就會使用自訂DITA-OT外掛程式來產生所需的輸出。

如果您想在發佈任何輸出時處理Ant引數，AEM Guides會為您提供簡單的方法。 您可以指定要使用哪些Ant引數，然後由發佈程式處理。

>[!NOTE]
>
> AEM Guides隨附DITA-OT 3.3.2版，但支援從DITA-OT 1.7到DITA-OT 4.x的一系列版本。如需DITA-OT版本的完整清單，請參閱[DITA-OT版本](http://www.dita-ot.org/download)。

>[!TIP]
>
> 如需使用自訂DITA-OT外掛程式的最佳作法，請參閱最佳作法指南中的&#x200B;*DITA-OT設定檔組態*&#x200B;和&#x200B;*使用自訂DITA-OT*&#x200B;區段。

## 使用自訂DITA-OT外掛程式 {#id181NH1020L7}

您可以將自訂DITA-OT外掛程式上傳至AEM存放庫，以使用自訂DITA-OT外掛程式進行發佈。 依預設，AEM Guides附帶預先設定的設定檔，其中包含用於編輯和發佈內容的預設範本設定。 您可以使用在編輯檔案時使用的自訂範本來建立自訂設定檔，並使用自訂DITA-OT外掛程式來發佈內容。

AEM Guides提供的預設DITA-OT套件附帶Apache FOP XSL-FO處理器，該處理器不支援轉譯MathML方程式。 如果您在內容中使用MathML方程式，請確定您已整合Apache FOP適用的MathML轉譯引擎外掛程式，或使用其他XSL-FO處理器。

執行以下步驟，將自訂DITA-OT外掛程式上傳至AEM存放庫：

1. 從歡迎電子郵件中共用的連結下載DITA-OT.zip檔案。

1. 解壓縮您系統上的zip檔案內容。

1. 使用DITA-OT外掛程式整合器機制，將新版DITA-OT與自訂DITA-OT外掛程式整合。

1. 再次建立ZIP檔案，保留相同的名稱\(`DITA-OT.ZIP`\)和資料夾結構。

1. 將更新後的ZIP檔案上傳回AEM存放庫。

   上傳ZIP檔案之前，請先確認下列檢查：

   - 在Mac/Linux作業系統上執行整合程式\（以安裝自訂外掛程式\），以避免檔案分隔符號發生問題，因為Windows和Linux作業系統有不同的檔案分隔符號，所以在Mac/Linux作業系統上整合的外掛程式會與Windows和Linux安裝程式相容。
   - 確定`DITA-OT.ZIP`檔案包含名為「DITA-OT」的資料夾，其中包含所有相關的外掛程式和檔案。
   - 檢查您建立的`DITA-OT.ZIP`檔案是否為mimeType： &quot;nt：file&quot; \(這與上傳至AEM時的ZIP檔案主要型別相對應\)。 使用WebDAV工具或程式碼部署，將此ZIP檔案上傳至AEM中的所需路徑。 \(請勿使用AEM的封裝管理員來部署此ZIP檔案，因為此ZIP不是AEM內容封裝，而只是封存檔案。\)

   >[!NOTE]
   >
   > 建議不要覆寫預設的DITA-OT套件。 您應該上傳包含外掛程式/var/dxml/dita\_resources/dita-ot資料夾的自訂DITA-OT套件。 您也可以使用Cloud Manager管道來執行此操作。如需詳細資訊，請參閱AEM檔案中的[部署至AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=zh-Hant)。

1. 您可以選擇編輯「預設設定檔」、建立新設定檔，或從「預設設定檔」複製設定以建立新設定檔。

   >[!NOTE]
   >
   > 您可以更新預設設定檔，但無法刪除它。 但是，您可以編輯和刪除您建立的所有新設定檔。

1. 設定下列屬性以使用自訂DITA-OT外掛程式：

   | 屬性名稱 | 說明 |
   |-------------|-----------|
   | **設定檔屬性** |
   | 設定檔名稱 | 為此設定檔提供唯一名稱。 |
   | 重複使用輸出 | *\（選擇性\）*&#x200B;如果您的設定檔是以現有的設定檔為基礎，請選取此選項。 選取此選項可確保AEM Guides不會再次擷取DITA-OT套件的內容，並重複使用現有的DITA-OT套件。 |
   | 設定檔擷取路徑 | *\(Optional\)*&#x200B;指定DITA-OT保留在磁碟上的路徑。 依預設，AEM Guides會將DITA-OT套件組合在其存放庫中，並透過此路徑擷取到磁碟上。<br> **注意**&#x200B;您可以使用任何現有的系統變數或屬性來定義此路徑。 如需詳細資訊，請參閱[DITA-OT環境變數](#id181NH0YN0AX)屬性的描述。 |
   | 指派的路徑 | \（*選擇性*\）指定此設定檔適用的內容存放庫路徑。 您可以指定多個位置。 |
   | **DITA-OT屬性** |
   | DITA-OT逾時 | \（*選擇性*\）指定AEM Guides等待DITA-OT外掛程式回應的時間\（以秒為單位）。 如果在指定時間內未收到任何回應，AEM Guides會終止發佈工作，且工作會標籤為失敗。 此外，輸出產生記錄檔中也有失敗記錄檔。 <br>預設值： 300秒\（5分鐘\） |
   | dita-OT PDF引數 | 指定由自訂DITA-OT外掛程式處理以產生PDF輸出的命令列引數。 對於所有自訂DITA-OT設定檔，請指定下列命令列引數： `-lib plugins/org.dita.pdf2.fop/lib/` |
   | dita-OT AEM引數 | \（*選擇性*\）指定自訂DITA-OT外掛程式處理用來產生AEM網站輸出的自訂命令列引數。 |
   | DITA-OT程式庫路徑 | \（*選擇性*\）指定DITA-OT外掛程式的其他程式庫路徑。 |
   | DITA-OT建置XML | \（*選擇性*\）指定自訂DITA-OT外掛程式隨附的自訂Ant建置指令碼路徑。 此路徑相對於檔案系統上的DITA-OT目錄。 |
   | DITA-OT Ant指令碼資料夾 | \（可選\）指定DITA-OT Ant指令碼資料夾的路徑。 此路徑相對於檔案系統上的DITA-OT目錄。 |
   | dita-OT環境變數 | *\（選擇性\）*&#x200B;指定要傳遞至DITA-OT處理程式的環境變數。 依預設，AEM Guides新增四個變數 — `ANT_OPTS`、`ANT_HOME`、`PATH`和`CLASSPATH`。 <br>您可以重複使用任何現有的系統環境變數或屬性來建置新的環境變數。 例如，如果您在系統中定義了`JAVA_HOME`系統變數，並且想要定義名為`JAVA_BIN`的新環境變數（使用`JAVA_HOME`建置）。 然後，您可以將`JAVA_BIN`的定義新增為：`JAVA_BIN= ${JAVA_HOME}/bin` <br> **注意：**&#x200B;您也可以使用Java系統屬性來建置環境變數。 例如，如果AEM啟動指令碼將Java系統屬性`java.io.tmpdir`定義為暫存目錄，您可以使用此屬性將新變數定義為： `${java.io.tmpdir}/fmdita/dita_ot`。<br> **重要：**&#x200B;若要重複使用任何現有的系統變數或屬性，必須將其括在`${}`內。 |
   | 覆寫DITA-OT輸出 | 選擇是否應覆寫DITA-OT輸出。 保持選取此選項。 |
   | AEM DITA-OT Zip路徑 | 指定自訂DITA-OT.zip檔案儲存在AEM存放庫中的完整路徑。 |
   | DITA-OT外掛程式路徑 | 自訂外掛程式的路徑。 此外掛程式會自動與主要DITA-OT套件整合。 |
   | 整合目錄 | \(*Optional*\) AEM存放庫中自訂DTD和XSD catalog.xml檔案的路徑。 只有在DITA-OT套件中遺失目錄時，才應提供此專案。 這些目錄會作為外掛程式自動與主要DITA-OT整合。 |
   | 新增系統ID目錄 | \（*選擇性*\）只有在目錄中有遺失的公用ID專案，或DITA檔案僅使用相對於其上傳來源伺服器路徑的系統ID時，才選取此選項。 |
   | DITA-OT暫時路徑 | 複製DITA檔案以供處理的暫存位置。 在DITA-OT處理檔案之前，會先在此暫存位置複製檔案。 預設的暫存位置為： <br> `<*AEM-Install*>/crx-quickstart/profiles/ditamaps` <br> **重要：**&#x200B;您不可變更預設路徑。 |

   >[!NOTE]
   >
   > AEM Guides安裝程式會建立兩個環境變數，可用來指定自訂DITA-OT外掛程式檔案的路徑。 這些環境變數為： `DITAOT\_DIR`，其中包含檔案系統上DITA-OT目錄的路徑；以及`DITAMAP\_DIR`，其中包含檔案系統擷取DITA map內容的路徑。

1. 按一下&#x200B;**完成**&#x200B;以儲存設定檔。


## 整合DITA專業化 {#id211MB0E00XA}

DITA專業化是透過新增元素或移除現有元素來建立新DITA結構的程式。 若要建立新的DITA元素，您可以以現有DITA元素為基底，並根據編寫需求對其進行修改。 本質上，DITA專業化可讓您建立符合業務需求的自訂資訊模型，同時保留現有DITA架構的優點。

您可以使用設定檔功能來儲存自訂DITA專業化設定。 接著，您就可以在編寫及發佈自訂DITA內容時，使用這些設定。 AEM Guides可讓您在自訂DTD/XSD中使用公用ID和系統ID。

>[!NOTE]
>
> AEM Guides Web Editor不支援XSD。

執行以下步驟來建立新設定檔，並將其設定為在AEM Guides中使用專門的DTD和XSD：

1. 在本機電腦上建立包含專用DTD和XSD的專用資料夾。

1. 在`catalog.xml`檔案中指定DTD詳細資料，這些詳細資料也必須包含在專業化資料夾中。

   >[!NOTE]
   >
   > 若是DITA 1.3，AEM存放庫中DTD `catalog.xml`檔案的預設位置為： `/libs/fmdita/dita_resources/DITA-1.3/dtd/catalog.xml`。

1. 在`catalog.xml`檔案中指定XSD詳細資料，這些詳細資料也必須包含在特殊化資料夾中。

   >[!NOTE]
   >
   > 若是DITA 1.3，AEM存放庫中XSD catalog.xml檔案的預設位置為： `/libs/fmdita/dita_resources/DITA-1.3/xsd/catalog.xml`。

1. 上傳資料夾至下列位置：

   `/var/dxml/dita_resources`

1. 按一下頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。

1. 從工具清單中選取&#x200B;**參考線**。

1. 按一下&#x200B;**DITA設定檔**&#x200B;圖磚。

1. 您可以選擇編輯「預設設定檔」、建立新設定檔，或從「預設設定檔」複製設定以建立新設定檔。

   >[!NOTE]
   >
   > 您無法刪除預設設定檔。 但是，您可以編輯和刪除您建立的所有新設定檔。

1. 在&#x200B;**結構描述** \> **目錄**&#x200B;設定中，指定您AEM存放庫中自訂DTD和XSD `catalog.xml`檔案的路徑。

1. 選取&#x200B;**新增系統識別碼目錄**&#x200B;選項。

   >[!NOTE]
   >
   > 僅當目錄中有遺失的公用ID專案，或DITA檔案僅使用相對於其上傳來源本機檔案路徑的系統ID時，才選取此選項。

   如需「設定檔」頁面上其他屬性的詳細資訊，請參閱[使用自訂DITA-OT外掛程式](#id181NH1020L7)區段的[步驟6](#id17A9F0D075Z)中的屬性表格。

1. 按一下&#x200B;**完成**&#x200B;以儲存設定檔。
