---
title: 支援Schematron檔案
description: 瞭解如何匯入及驗證DITA主題、使用判斷提示報表陳述式來檢查規則、使用規則運算式，以及在AEM Guides的Schematron檔案中定義抽象模式。
exl-id: ed07a5ec-6adc-43a3-8f03-248b8c963e9a
feature: Authoring, Features of Web Editor
role: User
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 0%

---

# 支援Schematron檔案

「Schematron」是指用於定義XML檔案測試的規則型驗證語言。 網頁編輯器支援Schematron檔案。 您可以匯入Schematron檔案，也可以在Web編輯器中編輯它們。 使用Schematron檔案，您可以定義某些規則，然後針對DITA主題或地圖驗證這些規則。

>[!NOTE]
>
> 網頁編輯器支援ISO架構。


## 匯入Schematron檔案

執行以下步驟來匯入Schematron檔案：

![](images/scematron-panel-add.png){width="300" align="left"}

1. 在&#x200B;*存放庫檢視*&#x200B;中導覽至所需的資料夾（您要上傳檔案的位置）。
1. 按一下&#x200B;**選項**&#x200B;圖示以開啟內容功能表，然後選擇&#x200B;**上傳Assets**。
1. 在&#x200B;**上傳Assets**&#x200B;對話方塊中，您可以在&#x200B;**選取資產資料夾**&#x200B;欄位中變更目的地資料夾。
1. 按一下&#x200B;**選擇檔案**&#x200B;並瀏覽以選取Schematron檔案。 您可以選取一或多個Schematron檔案，然後按一下[上傳]。****

## 使用Schematron驗證DITA主題或地圖

匯入Schematron檔案後，您可以在Web編輯器中編輯它們。 您可以使用Schematron檔案來驗證主題或DITA map。 例如，您可以為DITA map或主題建立下列規則：

* 已為DITA map定義標題。
* 已新增特定長度的簡短說明。
* 地圖中應至少有一個topicref。

當您在網頁編輯器中開啟主題時，右側會出現「架構驗證」面板。 執行以下步驟，使用Schematron檔案新增並驗證主題或地圖：
![](images/schematron-validate.png){width="300" align="left"}

1. 按一下「結構描述」圖示()以開啟「結構描述」面板。
1. 使用「新增Schematron檔案」來新增Schematron檔案。
1. 如果Schematron檔案沒有錯誤，則會新增並列在「驗證」面板中。 對於包含錯誤的Schematron檔案，會顯示錯誤訊息。
   >[!NOTE]
   >
   >您可以使用Schematron檔案名稱附近的十字圖示來移除它。
1. 按一下使用結構描述進行驗證，以驗證主題。

   * 如果主題未破壞任何規則，則會顯示檔案的驗證成功訊息。
   * 如果主題破壞規則，例如，如果它不包含標題並為上述給定結構描述驗證，它會顯示驗證錯誤。

1. 按一下錯誤訊息，在開啟的主題/地圖中反白顯示包含錯誤的元素。

網頁編輯器中的Schematron支援可協助您根據一組規則來驗證檔案，並維護主題間的一致性和正確性。

## 使用判斷提示和報表陳述式來檢查規則{#schematron-assert-report}

AEM Guides也支援Schematron中的判斷提示和報表陳述式。 這些陳述式可協助您驗證DITA主題。

### Assert陳述式

當測試陳述式評估為false時，判斷提示陳述式會產生訊息。 例如，如果您希望標題為粗體，可以為其定義判斷提示陳述式。

```XML
<sch:rule context="title"> 
    <sch:assert test = "b"> Title should be bold </sch:assert>
  </sch:rule>
```

當您使用結構描述驗證DITA主題時，您會收到標題不是粗體的主題訊息。

### 報表陳述式

當測試陳述式評估為true時，報表陳述式會產生訊息。 例如，如果您希望簡短說明少於或等於150個字元，可以定義報表陳述式，以檢查簡短說明超過150個字元的主題。
使用結構描述驗證DITA主題時，您會獲得規則完整的報告，其中報告陳述式的評估為true。 因此，您會收到一則主題訊息，其中簡短說明超過150個字元。


```XML
<sch:rule context="shortdesc"> 
        <sch:let name="characters" value="string-length(.)"/> 
        <sch:report test="$characters &gt; 150">  
        The short description has <sch:value-of select="$characters"/> characters. It should contain more than 150 characters.      
        </sch:report>   
    </sch:rule> 
```

>[!NOTE]
>
> 寫入Schematron規則時只使用Xpath 2.0運算式。

## 使用規則運算式{#schematron-regex-espressions}

您也可以使用Regex運算式定義具有matches()函式的規則，然後使用Schematron檔案執行驗證。

例如，如果標題只包含一個單字，您可以使用它來顯示訊息。

```XML
<assert test="not(matches(.,'^\w+$'))"> 
No one word titles.
</assert>  
```


## 定義抽象模式{#schematron-abstract-patterns}

AEM Guides也支援Schematron中的抽象模式。 您可以定義一般抽象模式，重複使用這些抽象模式。  您可以建立指定實際模式的預留位置引數。


使用抽象模式可減少規則的重複，並更容易管理和更新驗證邏輯，藉此簡化您的Schematron方案。 它也能讓您的結構描述更易於理解，因為您可以在可在整個結構描述中重複使用的單一抽象模式中定義複雜的驗證邏輯。


例如，下列XML程式碼會建立抽象模式，然後實際模式會使用id來參照它。

```XML
<sch:pattern abstract="true" id="LimitNoOfWords"> 

<sch:rule context="$parentElement"> 

<sch:let name="words" value="string-length(.)"/> 

<sch:assert test="$words &lt; $maxWords"> 

You have <sch:value-of select="$words"/> letters. This should be lesser than <sch:value-of select="$maxWords"/>. 

</sch:assert>  

<sch:assert test="$words &gt; $minWords"> 

You have <sch:value-of select="$words"/> letters. This should be greater than <sch:value-of select="$minWords"/>. 

</sch:assert>  

</sch:rule> 

</sch:pattern> 

<sch:pattern is-a="LimitNoOfWords" id="extend-LimitNoOfWords"> 

<sch:param name="parentElement" value="title"/> 

<param name="minWords" value="1"/> 

<param name="maxWords" value="8"/> 

</sch:pattern> 
```
