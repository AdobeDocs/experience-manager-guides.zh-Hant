---
title: AEM Guides中的DITA內容重複使用
description: 此簡短文章說明AEM Guides和DITA如何協助您在使用內容重複使用性時節省時間和精力
role: User, Admin
author: Pulkit Nagpal(punagpal)
exl-id: 1522ebf5-2aea-4d8f-ade7-367227b31dd9
source-git-commit: f971be4be9e2d32618616727cd9c682941dd3fb2
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# AEM Guides中的內容重複使用性

AdobeAEM Guides運用DITA的長處，提供使用者易用的介面以重複使用內容。

本文將討論：

1. [使用主題參考可重複使用(](#reusability-using-topic-referencestopicref)
2. [使用內容參考的可重複使用性(](#reusability-using-content-reference-conref--conkeyref)
3. [在AEM Guides中拖放以重複使用內容的額外秘訣](#reuse-content-with-a-single-click-in-aem-guides)

## 使用主題參照(topicref)可重複使用



假設您是一間製造公司，擁有安全預防或疑難排解技巧的一般主題。

這些可在每個機器型號的特定使用者手冊中參考和改寫，減少備援並確保核心安全資訊保持一致。

```
<map id="user_manual_model 100" title="ABC Model 100 User Manual ">


<topicref href="Safety_Information.dita" format="dita">
</topicref>
.
.
.
.
.
</map>
```


同樣適用於Model 200

```
<map id="user_manual_model 200" title="ABC Model 200 User Manual ">

<topicref href="Safety_Information.dita" format="dita">
</topicref>
.
.
.
.
.
  
</map>
```

## 使用內容參考可重複使用(conref &amp; conkeyref)

內容參照(conref)屬性可讓您連結至內容的其他部分。 如此可提升可重複使用性，並減少備援。

例如：

假設您是一家金融企業，並且有一個通用的KYC主題，其中包含適用於個人、公司等的KYC程式。

您想要針對「儲存帳戶」和「需求帳戶」主題重複使用個別KYC片段。

```
<section id="kyc_requirements_saving_account">
  <title>Know Your Customer (KYC) Requirements</title>
  <p>To comply with regulations and ensure customer identification, all individual applicants for savings  accounts must fulfill the KYC requirements as outlined below</p>
  <p conref=kyc_procedures.dita#individual_kyc></p>
</section>
```

此處`conref=kyc_procedures.dita#indvidual_kyc` kyc_procedures.dita是檔案識別碼，#individual_kyc是片段識別碼。

Kyc_procedure.dita仍然是唯一的資訊來源。 如果法規變更需要更新KYC程式，請使用新的路徑更新主題路徑。 這些變更會自動反映在所有參照它的主題中。

使用AEM Guides時，只要按兩下

步驟1：按一下「插入可重複使用的內容」
![工具列](../../assets/publishing/content-reusability_image1.png)

<br>

步驟2：選取需要重複使用的檔案和片段。
![conref](../../assets/publishing/content-reusability_image2.png)

與「conref」類似，您也可以使用「conkeyref」，除了提供內容路徑以外，您還可以透過索引鍵參考內容

程式碼範例：

```
<section conkeyref="kyc_procedure/individual_kyc_procedure" id="individual_kyc_procedure"></section>
```

金鑰定義如下：

```
<map id="ABC_manual">
  <title>ABC_Manual</title>
  <topicref href="kyc_procedure_2020.dita" keys="kyc_procedure" processing-role="resource-only" type="concept">
  </topicref>
  <topicref href="savings_account.dita" type="concept">
  </topicref>
</map>
```

索引鍵 — &#39;Kyc_procedure&#39;仍然是單一資訊來源。 如果根據法規要求對KYC流程有任何變更，您只需要以新主題路徑更新一個主題路徑，這些變更會自動反映在引用它的所有主題中。

```
<map id="ABC_manual">
  <title>ABC_Manual</title>
  <topicref href="kyc_procedure_2024.dita" keys="kyc_procedure" processing-role="resource-only" type="concept">
  </topicref>
  <topicref href="savings_account.dita" type="concept">
  </topicref>
</map>
```

在此處，由於最近的規則變更，主題路徑已從「kyc_procedure_2020.dita」變更為「kyc_procedure_2024.dita」。

使用AEM Guides時，只要按兩下

步驟1：按一下「插入可重複使用的內容」
![工具列](../../assets/publishing/content-reusability_image1.png)

步驟2：選取您的根對應（選用）、金鑰以及需要重複使用的片段。
![conkeyref](../../assets/publishing/content-reusability_image3.png)

在此處，由於根對映已在對映檢視中開啟，因此已自動選取根對映。


## 在AEM Guides中按一下即可重複使用內容

AEM Guides提供「可重複使用的內容」功能，只需按一下即可新增內容參考。

步驟1：將通用主題新增至可重複使用的內容

![新增可重複使用的內容](../../assets/publishing/content-reusability_image4.png)

步驟2：新增後，拖放您要在任何目的地主題中重複使用的片段。

![新增可重複使用的內容gif](../../assets/publishing/content-reusability_image5.gif)



## 常見問題集

- ### 在「重複使用內容」對話方塊中選擇檔案/金鑰後，所有內容都未顯示

將ID指派給您想在其他主題中重複使用的片段（Dita元素）

- ## 金鑰未顯示在「重複使用內容」對話方塊中

  請確定您已在地圖檢視中開啟根對應/父對應，它具有索引鍵定義，或在同一個對話方塊中手動新增根對映路徑。


<br>
<br>
<br>


在AEM Guides社群[論壇](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation?profile.language=zh-Hant)上發佈任何查詢。
