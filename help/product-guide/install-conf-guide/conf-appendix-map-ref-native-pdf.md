---
title: 在原生PDF輸出中設定地圖參考的附錄演算
description: 瞭解如何設定Experience Manager Guides，將附錄中子地圖下方新增的主題轉譯為原生PDF輸出的附錄內容。
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 63ae0f947d50646bed34cd815db6b9fb585fc015
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%
---

# 在原生PDF輸出中設定地圖參考的附錄演算

在原生PDF輸出中，`<appendix>`元素內的子地圖中參照的主題可以呈現為章節而非附錄。 依預設，Experience Manager Guides會依元素名稱來分類地圖參考，而在處理期間將地圖平面化後，相關資訊便會遺失。

使用此設定可改用DITA-OT產生的`class`屬性來分類對應參考。 然後，附錄子地圖中的主題轉譯為附錄。

>[!NOTE]
>
>此設定會變更對應參考的分類方式。 預設為停用。 只有當您的內容在`<appendix>`內的子地圖中放置主題，而且您看到它們在Native PDF輸出中呈現為章節時，才啟用它。

## 何時使用此設定

請考量下列書籍地圖的範例：

- `<appendix>`元素直接參考主題。 這些主題會在產生的PDF中呈現為附錄。

  ```XML
  <booktitle>
      <mainbooktitle>Product Guide</mainbooktitle>
    </booktitle>
    <frontmatter>
      <booklists>
        <toc/>
        <tablelist/>
      </booklists>
      <preface href="topics/preface.dita">
      </preface>
    </frontmatter>
    <chapter class="foo" href="topics/getting-started.dita">
    </chapter>  
    <appendix href="topics/appendix-reference-tables.dita">
    </appendix>
    <appendix href="topics/appendix-troubleshooting.dita">
    </appendix>
    <backmatter>
      <booklists>
        <indexlist/>
      </booklists>
    </backmatter>
  </bookmap>`
  ```

- 另一個`<appendix>`元素參考子對映，而子對映參考使用`<topicref>`的主題。

  ```xml
  <booktitle>
      <mainbooktitle>Product Guide</mainbooktitle>
    </booktitle>
    <frontmatter>
      <booklists>
        <toc/>
        <tablelist/>
      </booklists>
      <preface href="topics/preface.dita">
      </preface>
    </frontmatter>
    <chapter class="foo" href="topics/getting-started.dita">
    </chapter>  
    <appendix format="ditamap" href="submap-for-appendix.ditamap" type="map">
    </appendix>
    <backmatter>
      <booklists>
        <indexlist/>
      </booklists>
    </backmatter>
  </bookmap>
  ```

  附錄的子地圖：

  ```xml
  <map id="GUID-cc306264-825c-455e-89db-d27af9197a2f">
    <title>submap-for-appendix</title>
    <topicref href="topics/appendix-reference-tables.dita" type="reference">
    </topicref>
    <topicref href="topics/appendix-troubleshooting.dita" type="topic">
    </topicref>
  </map>
  ```

若沒有此設定，第一個附錄的主題會呈現為附錄，但子地圖的主題會呈現為章節。 只會發佈主題；子地圖本身會用於階層，不會出現在輸出中。

## 進行設定

以下是設定此設定的指示：

1. 使用[組態覆寫](../install-conf-guide/download-install-config-override.md)中提供的指示來建立組態檔。

2. 在設定檔案中，提供下列（屬性）詳細資訊：

   | PID | 屬性索引鍵 | 屬性值 |
   | --------------------------------------- | -------------------------------- | ----------------------------- |
   | `com.adobe.fmdita.config.ConfigManager` | `guides.publish.config` | {USE_DITA_OT_GENERATED_CLASS&quot;： false} |

3. 將值設為`true`以啟用設定，並使用Cloud Manager部署組態。