---
title: 為自訂Dita型別設定圖示
description: 瞭解如何為自訂Dita型別定義圖示，以便在AEM中的不同UI上顯示其圖示
source-git-commit: ce2f5e4ab6b05fbce7b8384ff59091ebf9bab7be
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# 為自訂Dita （主題或地圖）型別設定圖示


## 問題陳述

使用AEM Guides中使用的自訂結構，您可以建立自訂主題或地圖型別，並可能會注意到自訂主題/地圖不會在網頁編輯器或Assets UI中顯示圖示。 如需參考資訊，請參閱熒幕擷圖  (../assets/authoring/custom-ditatype-icon-notshown.png)

因此，若要將圖示指派給自訂主題/地圖型別，您必須執行以下操作：
- 尋找自訂主題/地圖型別
- 撰寫樣式以新增自訂型別的所需圖示


我們可以實作上述步驟，在網頁編輯器（存放庫檢視）和資產UI中顯示圖示。 以下是兩者的步驟


## 在網頁編輯器檢視中顯示自訂主題/對應的圖示

步驟1 ：決定自訂Dita主題/ap的Dita型別 — 在Web編輯器中開啟存放庫檢視>在瀏覽器上開啟開發人員主控台 — Inspect所列出主題/map旁的圖示空間 — 檢查指派給自訂主題的類別 — 參閱熒幕擷圖  (../assets/authoring/custom-ditatype-icon-knowditatype.png)以取得詳細資料 — 我們將使用此類別來指派圖示並寫入css

步驟2：建立css並將圖示指派給此dita型別 — 在/apps下建立使用者端程式庫，例如您在想要的路徑下建立cq：ClientLibraryFolder — 將類別「apps.fmdita.xml_editor.page」新增至其中 — 在此目錄下建立資料夾「assets」，並新增您要用於自訂dita型別的所有圖示 — 在使用者端程式庫資料夾下新增css檔案，例如「tree-icons.css」 — 新增下列程式碼

```
            .tree-item-icon {
                &.custommaptype {
                    background-image: url('assets/custommap.svg')
                }
                &.customtopictype {
                    background-image: url('assets/customtopic.svg')
                }
            }
```

     — 在client library資料夾下新增css.txt，並新增剛才建立「tree-icon.css」的參照
     — 儲存/部署這些變更
參考熒幕擷圖  (../assets/authoring/custom-ditatype-icon-define-webeditor-styles.png)以取得詳細資訊。

而最終輸出會顯示在熒幕擷圖中  (../assets/authoring/custom-ditatype-icon-webeditor-showstyles.png)


## 顯示資產UI中自訂主題/對應的圖示

步驟1：決定自訂dita主題/map的dita型別 — 這已在先前方法的步驟1中說明

步驟2：建立Javacscript以定義要針對自訂dita型別載入哪些圖示 — 在/apps下建立使用者端程式庫，例如您在所需路徑下建立cq：ClientLibraryFolder — 新增下列屬性： - &quot;categories&quot;(multivalue string)值作為&quot;dam.gui.admin.coral&quot; - &quot;dependencies&quot;(multivalue string)值作為&quot;libs.fmdita.versioncontrol&quot; — 將檔案&quot;/libs/fmdita/clientlibs/clientlibs/xmleditor/clientlib-dam/topic_type.js&quot;複製到此/apps目錄 — 編輯複製的&quot;topic_type.js&quot;，並在&quot;type變數下變更/add customtopictopictypeNameNameName map」 — 您還可以更改影象資料夾的路徑，方法是將變數「parentImagePath」的值更改為儲存自定義圖示的位置 — 在client library資料夾下建立名為js.txt的檔案並新增對「topic_type.js」的引用 — 儲存/部署這些更改參考螢幕快照  (../assets/authoring/custom-ditatype-icon-define-assetsui-styles.png)以取得詳細資訊。

而最終輸出將會如熒幕擷圖中所示  (../assets/authoring/custom-ditatype-icon-assetsui-showstyles.png)