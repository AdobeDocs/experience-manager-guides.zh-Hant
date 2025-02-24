---
title: 後續處理事件處理常式
description: 瞭解後處理事件處理常式
exl-id: 3b105ff5-02d4-40e3-a713-206a7fcf18b2
feature: Post-Processing Event Handler
role: Developer
level: Experienced
source-git-commit: 8c992afc1cc56052e6c07ac3cea6e7d3412259b2
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 5%

---

# 後續處理事件處理常式 {#id175UB30E05Z}

## UUID和Cloud Service

Adobe Experience Manager Guides公開用於執行任何後處理操作的`com/adobe/guides/postprocess/complete`事件。 只要對DITA檔案執行作業，就會觸發此事件。 對DITA檔案的下列操作會觸發此事件：

- 上傳
- 建立
- 修改


您需要建立Adobe Experience Manager事件處理常式，以讀取此事件中可用的屬性，並進行進一步處理。

事件詳細資訊說明如下：

**事件名稱**：

```
com/adobe/guides/postprocess/complete 
```

**引數**：

| 名稱 | 類型 | 描述 |
|----|----|-----------|
| `path` | 字串 | 觸發此事件的檔案路徑。 通常，這是已對其執行操作的檔案。 |
| `eventType` | 字串 | 事件型別，即CREATE或MODIFY。 |
| `status` | 字串 | 已執行作業的傳回狀態。 可能的選項包括： - <br>- SUCCESS：已成功完成後續處理作業。 <br> — 失敗：因為發生某些錯誤，後處理作業失敗。 |
| `errorMsg` | 字串 | 發生後置處理作業失敗時的錯誤訊息。 |
| `uuid` | 字串 | 觸發此事件的檔案UUID。 通常，這是已對其執行操作的檔案。 |

**範例事件接聽程式**


```
@Component(service = EventHandler.class,
        immediate = true,
        property = {
                EventConstants.EVENT_TOPIC + "=" + "com/adobe/guides/postprocess/complete",
        })
public class PostProcessCompleteEventHandler implements EventHandler {

    protected final Logger log = LoggerFactory.getLogger(this.getClass());

    @Override
    public void handleEvent(final Event event) {
        Set<String> propertyNames = new HashSet<>(Arrays.asList(event.getPropertyNames()));
        Map<String, String> properties = new HashMap<>();
        properties.put("path", (String) event.getProperty("path"));
        properties.put("eventType", (String) event.getProperty("eventType"));
        properties.put("status", (String) event.getProperty("status"));
        if(propertyNames.contains("errorMsg")) {
            properties.put("errorMsg", (String) event.getProperty("errorMsg"));
        }
        if (propertyNames.contains("uuid")) {
            properties.put("uuid", (String) event.getProperty("uuid"));
        }
        String eventTopic = event.getTopic();
        log.debug("eventTopic {}", eventTopic);
        for(Map.Entry entry:properties.entrySet()) {
            log.debug(entry.getKey() + " : " + entry.getValue());
        }
    }
}
```

## 非UUID


Adobe Experience Manager Guides會公開用於執行任何後處理操作的com/adobe/fmdita/postprocess/complete事件。 只要對DITA檔案執行作業，就會觸發此事件。 對DITA檔案的下列操作會觸發此事件：

>[!NOTE]
>
> AEM 6.1中的刪除作業不會觸發此事件。

- 上傳
- 建立
- 修改
- 刪除

您需要建立Adobe Experience Manager事件處理常式，以讀取此事件中可用的屬性，並進行進一步處理。

事件詳細資訊說明如下：

**事件名稱**：

```
com/adobe/fmdita/postprocess/complete 
```

**引數**：

| 名稱 | 類型 | 描述 |
|----|----|-----------|
| `path` | 字串 | 觸發此事件的檔案路徑。 通常，這是已對其執行操作的檔案。 |
| `status` | 字串 | 已執行作業的傳回狀態。 可能的選項包括： - <br>- SUCCESS：已成功完成後續處理作業。 <br> — 已完成，但發生錯誤：後處理作業已完成，但發生一些錯誤。 <br> — 失敗：因為發生某些錯誤，後處理作業失敗。 |
| `message` | 字串 | 如果狀態為COMPLETED WITH ERRORS或FAILED，此引數包含有關錯誤或失敗原因的詳細資訊。 |
| `operation` | 字串 | 對檔案執行的後處理操作。 可能的選項包括：<br> — 新增<br> — 更新<br> — 刪除 |
