---
title: AEM Guides發行版本
description: AEM Guides 最新發行版本和必備的 AEM 版本
exl-id: 780697a9-bdc6-40c2-b258-64639fe30f88
feature: Release Notes
role: Leader
source-git-commit: 60fb990158b562825e18a9691430dbfe7836422b
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 1%

---

# [!DNL AEM Guides]版本

[!DNL Adobe Experience Manager Guides]是部署至AEM的應用程式。 這是一個功能強大、企業級元件內容管理解決方案(CCMS)；此解決方案啟用Adobe Experience Manager的原生DITA支援、使AEM能夠處理以DITA為主的內容建立和傳遞。

AEM Guides套件有兩種變體可用 — UUID組建和非UUID組建。

## UUID和非UUID組建

UUID和非UUID組建之間的主要差異如下：

|  | 非UUID版本編號 | UUID建置 |
|---|---|---|
| **資產識別** | 所有資產都是使用存放庫中資產的路徑來識別。 | 所有資產都使用其UUID （資產首次上傳時系統產生的唯一ID）識別。 |
| **參考建立** | 所有內容參照都是根據其路徑建立的。 | 所有內容參考都是根據其UUID建立。 |

### UUID建置的優點

* UUID安裝的效能較高：
   * 參照與路徑無關：參照管理系統會察覺到連結，因為參照是根據UUID而不是路徑建立的。
   * 移動/更新作業相當有效率：即使資產移至存放庫中的其他路徑，UUID仍會維持不變。 因此，在移動/更新作業中，不需要處理即可修補資產之間的引用。
* UUID組建具有前瞻性，因為我們也將此框架用於AEM Guides的雲端設定。


### 在兩個組建之間選擇

* 如果您是新客戶，建議您使用UUID版本編號。
* 如果您是現有客戶，您可以選擇移至UUID版本編號，因為現在可以從非UUID版本移轉至UUID版本編號。 如需詳細資訊，請參閱&#x200B;**安裝與設定Adobe Experience Manager Guides**&#x200B;中的&#x200B;*非UUID移轉至UUID內容移轉*&#x200B;區段。

>[!NOTE]
>
>* 客戶在第一次設定時，將需要在UUID和非UUID模式之間做出決定（若您需要協助，請聯絡客戶成功經理，協助您根據使用情況做出決定）。
>* 從某個AEM Guides版本升級至較新版本時，客戶需確保選擇相同模式（UUID /非UUID）以符合其現有模式。 非UUID組建不應直接升級至UUID組建。 從非UUID組建移轉至UUID組建將需要內容移轉。

**正在升級組建**

當您從較舊版本升級至較新版本的[!DNL AEM Guides]時，您可能需要執行移轉指令碼。 如需升級指示，請參閱版本注意事項和版本特定檔案。

並非所有升級路徑都直接受支援。 例如，只有從3.8版才能直接升級至4.0版。
如果您使用的是3.8之前的版本，請參閱版本專屬檔案以取得升級指示[說明封存](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)。
請洽詢您的客戶成功案例經理以驗證升級路徑。

**[!DNL AEM Guides]組建**

下列清單包含可在AMS或內部部署安裝的最新[!DNL AEM Guides]套件、對應的AEM版本（先決條件）、套件的下載連結以及其他實用資訊。 建議僅使用[!DNL AEM Guides]的最新組建。 如果由於某些原因，您需要存取較舊的組建，請聯絡您帳戶的客戶成功經理。

>[!NOTE]
>
>請聯絡您的客戶成功案例經理，以存取AEM as a Cloud Service的[!DNL AEM Guides]組建。

| [!DNL AEM Guides]版本 | 發行說明 | AEM必要條件 | 建立下載連結 |
|---|---|---|---|
| **AEM Guides 4.4.0** | [4.4.0升級指示](./upgrade-instructions-4-4.md)<br><br>[4.4.0新功能](./whats-new-4-4.md)<br><br> | **非UUID和UUID 4.4.0** <br>AEM 6.5 SP20、SP19、SP18或SP17 <br><br>   Java： 11或8 <br><br> **非UUID和UUID 4.4.0** <br>AEM 6.5 SP20、SP19、SP18或SP17 <br><br>   Java： 11或8 | **非UUID AEM 6.5** <br> [4.4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-4%2Fcom.adobe.fmdita-6.5-4.4.0.40.zip) <br> **UUID AEM 6.5** <br>[4.4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-4%2Fcom.adobe.fmdita-6.5-uuid-4.4.0.40.zip) |
| **AEM Guides 4.3.0** | [4.3.1.5升級指示](./upgrade-instructions-4-3-1-5.md)<br><br> [4.3.1發行說明](./release-notes-4-3-1.md)<br><br>[4.3.0發行說明](./release-notes-4-3.md) | **非UUID與UUID 4.3.1.5** <br>AEM 6.5 SP18、SP17、SP16、SP15或SP14 <br><br>   Java： 11或8 <br><br> **非UUID與UUID 4.3.1** <br>AEM 6.5 SP18、SP17、SP16、SP15或SP14 <br><br>   Java： 11或8 <br><br> **非UUID和UUID 4.3.0** <br>AEM 6.5 SP18、SP17、SP16、SP15或SP14 <br><br>   Java： 11或8 | **非UUID AEM 6.5** <br>[4.3.1.5](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3-1-5%2Fcom.adobe.fmdita-6.5-hotfix-4.3.1.5.1.zip)<br> [4.3.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3-1%2Fcom.adobe.fmdita-6.5-4.3.1.390.zip) <br> [4.3.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3%2Fcom.adobe.fmdita-6.5-4.3.0.347.zip)<br> **UUID AEM 6.5** <br>[4.3.1.5](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3-1-5%2Fcom.adobe.fmdita.uuid-6.5-hotfix-4.3.1.5.1.zip)<br> [4.3.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3-1%2Fcom.adobe.fmdita-6.5-uuid-4.3.1.390.zip)<br>[4.3.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3%2Fcom.adobe.fmdita-6.5-uuid-4.3.0.347.zip) |
| **AEM Guides 4.2** | [4.2.1發行說明](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/42-release/42-release-notes/release-notes-4.2.1.html?lang=en)<br> <br> [4.2發行說明](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/42-release/42-release-notes/release-notes-4.2.html?lang=en) | **非UUID和UUID 4.2.1**<br><br> AEM 6.5 SP15、SP14、SP13或SP12 <br><br>Java： 11或8 <br><br>**非UUID和UUID 4.2**<br><br> AEM 6.5 SP15、SP14、SP13或SP12 <br><br>Java： 11或8<br><br> | **非UUID**： <br> **AEM 6.5** <br>[4.2.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-2-1%2F4-2-1-non-uuid%2Fcom.adobe.fmdita-6.5-4.2.1.270.zip)<br>[4.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-2%2F4-2-non-uuid%2Fcom.adobe.fmdita-6.5-4.2.229.zip)<br><br> **UUID** <br>**AEM 6.5** <br>[4.2.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-2-1%2F4-2-1-uuid%2Fcom.adobe.fmdita-6.5-uuid-4.2.1.270.zip)<br>[4.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-2%2F4-2-uuid%2Fcom.adobe.fmdita-6.5-uuid-4.2.229.zip)<br> |
| **AEM Guides 4.1** | [4.1.x發行說明](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/release-notes-4.1.html) | **非UUID和UUID 4.1.2**<br><br> AEM 6.5 SP13、SP12、SP11或SP10 <br>Java： 11或8 <br><br>**非UUID和UUID 4.1**<br><br> AEM 6.5 SP13、SP12、SP11或SP10 | **非UUID**： <br> **AEM 6.5** <br>[4.1.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-3%2F4-1-3-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.1.3.2.zip)<br>[4.1.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-2%2F4-1-2-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.1.2.11.zip)<br>[4.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1%2F4-1-non-uuid%2Fcom.adobe.fmdita-6.5-4.1.159.zip)<br><br> **UUID** <br>**AEM 6.5** <br>[4.1.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-3%2F4-1-3-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.1.3.2.zip)<br>[4.1.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-2%2F4-1-2-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.1.2.11.zip)<br>[4.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1%2F4-1-uuid%2Fcom.adobe.fmdita-6.5-uuid-4.1.159.zip) |
| **AEM Guides 4.0** | [4.0.x發行說明](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-4-0.html) | **非UUID和UUID 4.0.3**<br> AEM 6.5 SP12、SP11、SP10或SP9 <br>Java： 11或8 <br><br> <br>**非UUID和UUID 4.0.2** <br> AEM 6.5 SP12、SP11、SP10或SP9 <br>Java： 11或8 <br><br> **非UUID與UUID 4.0** <br> AEM 6.5 SP11、SP10或SP9 | **非UUID**： <br> **AEM 6.5** <br>[4.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-3%2F4-0-2-non-uuid%2Fcom.adobe.fmdita-6.5-hotfix-4.0.3.1.zip)<br>[4.0.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-2%2F4-0-2-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.0.2.10.zip) <br> [4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/4-0/4-0-non-uuid/com.adobe.fmdita-6.5-4.0.70.zip) <br><br> **UUID** <br>**AEM 6.5** <br>[4.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-3%2F4-0-3-uuid%2Fcom.adobe.fmdita.uuid-6.5-hotfix-4.0.3.1.zip) <br>[4.0.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-2%2F4-0-2-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.0.2.10.zip)<br> [4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/4-0/4-0-uuid/com.adobe.fmdita-6.5-uuid-4.0.70.zip) |
| **AEM Guides 3.8.5** <br> 3.8.5是3.8之上的SP版本。<br>3.8發行版本不可獨立安裝，因為3.8.5 SP包含重要修正。 <br>客戶必須先安裝3.8，然後再安裝SP 3.8.5。 | [3.8.x發行說明](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-3-8.html) | **非UUID** <br> AEM 6.5 SP9或SP8 <br> AEM 6.4 SP8 <br> AEM 6.3 SP3 <br><br> **UUID** <br> AEM 6.5 SP9或SP8 | **非UUID**： <br> **AEM 6.5** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.5-hotfix-3.8.5.2.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.5-3.8.166.zip)<br> **AEM 6.4** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.4-hotfix-3.8.5.1.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.4-3.8.166.zip) <br> **AEM 6.3** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.3-hotfix-3.8.5.1.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.3-3.8.166.zip) <br><br> **UUID** <br>**AEM 6.5** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5uuid/com.adobe.fmdita.uuid-6.5-hotfix-3.8.5.2.zip) <br> [3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8uuid/com.adobe.fmdita.uuid-6.5-3.8.168.zip) |
