---
title: 大量啟用完成事件處理常式
description: 瞭解大量啟用完成事件處理常式
feature: Bulk Activation Event Handler
role: Developer
level: Experienced
exl-id: 08b153d7-3d13-4804-9e3e-38790dbea1f3
source-git-commit: 9b8971bf7065a94a2e42669094249c822c555718
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 6%

---

# 大量啟用完成事件處理常式

Experience Manager Guides會公開用於在大量啟動程式完成後執行任何作業的`com/adobe/fmdita/replication/complete`事件。 當大量啟用程式完成時，就會觸發此事件。 例如，如果您執行大量啟動地圖的AEM網站預設集，此事件會在啟動程式結束後呼叫。

您需要建立AEM事件處理常式，以讀取此事件中可用的屬性，並進行進一步處理。

事件詳細資訊說明如下：

**事件名稱**：

```
com/adobe/fmdita/replication/complete 
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `path` | 字串 | 觸發此事件的檔案路徑。 <br>例如，`/content/output/sites/ditamap1-ditamap`。 <br>這是序列化為JSON陣列的路徑清單。 |
| `messageType` | 字串 | 訊息的型別。 <br>可能的選項： `REPLICATION` |
| `action` | 字串 | 這是執行的動作。 <br>可能的選項： `BulkReplicate` |
| `user` | 字串 | 啟動作業的使用者。 |
| `result` | 字串 | 大量啟動的結果。 它是序列化JSON物件： <br>`{"success":boolean,"code":integer,"message":"" }` |
| `agentId` | 字串 | 復寫中使用的agentId。 例如，`"publish"`。 |
| `importMode` | 字串 | Activation中使用的匯入模式。 可能的選項包括： <br>`REPLACE, MERGE, UPDATE`。 |


**範例事件接聽程式**：

```XML
@Component(service = EventHandler.class,
        immediate = true,
        property = {
                EventConstants.EVENT_TOPIC + "=" + "com/adobe/fmdita/replication/complete",
        })
 
public class SampleEventHandler implements EventHandler {
 
    protected final Logger log = LoggerFactory.getLogger(this.getClass());
 
    @Override
    public void handleEvent(final Event event) {
        Map<String, String> properties = new HashMap<>();
        properties.put("paths", (String) event.getProperty("paths"));
        properties.put("messageType", (String) event.getProperty("messageType"));
        properties.put("action", (String) event.getProperty("action"));
        properties.put("result", (String) event.getProperty("result"));
        properties.put("user", (String) event.getProperty("user"));
        properties.put("agentId", (String) event.getProperty("agentId"));
        properties.put("importMode", (String) event.getProperty("importMode"));
 
        String eventTopic = event.getTopic();
        log.debug("eventTopic {}", eventTopic);
        for(Map.Entry entry:properties.entrySet()) {
            log.debug(entry.getKey() + " : " + entry.getValue());
        }
 
    }
}
```
