---
title: 建立翻譯專案
description: 瞭解如何建立API翻譯專案
feature: Post-Processing Event Handler
role: Developer
level: Experienced
source-git-commit: 41dd3dee5f9d64fb5c58b5b302cc9759e48e3631
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 15%

---

# 建立翻譯專案

POST方法可協助您接受所需專案詳細資訊，以建立翻譯專案。

## 請求 URL

`http://<aem-guides-server>:<port-number>/bin/guides/v1/translation/project/create`

## 請求類型

POST

## 要求引數

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `type` | 字串 | newTranslationProject， xliffTranslationProject， newMultiLingualTranslationProject， addToExistingProject， newScopingTranslationProject |
| `versionDetails`、`versionSelector` | 字串 | 比較基準， latestVersion， versionAsOfDate |
| `language` | 字串 | 逗號分隔語言「de」、「fr」 |
| `map.id` | 字串 | 要翻譯之來源地圖的GUID |
| `map.path` | 字串 | 要翻譯的來源對應路徑 |
| `referenceType` | 字串 | 間接、直接 |
| `fileType` | 字串 | 地圖、主題、其他 |
| `documentState` | 字串 | 可以是使用者在地圖設定檔上指派的清單之一 |
| `translationStatus` | 字串 | 不同步、正在同步、最新、過期、進行中、遺失副本、無、不適用 |

>[!NOTE]
>
>建立翻譯專案時，您可以使用`map.id`或`map.path`。

## 請求範例

```JSON
{
  "title": "Test Project 1 on Dec 5",
  "type": "newTranslationProject",
  "translationDetails": {
    "map": {
      "id": "GUID-06527014-062d-46dc-8fea-48b4b4497c51-en",
      "path": "/content/dam/ajay-test/lang/en/m2.ditamap"
    },
    "languages": ["de"],
    "versionDetails": {
      "versionSelector": "latestVersion"
    }
  },
  "filterDetails": [
    { "name": "referenceType", "values": [] },
    { "name": "fileType", "values": [] },
    { "name": "documentState", "values": [] },
    { "name": "translationStatus", "values": [] }
   ]
```

## 回應值

```JSON
{
  "executionId": "5c13c571-3407-46d5-8f45-50ea9e05a212",
  "path": "/content/projects/test_project_1_ondec5"
}
```

**回應代碼**

- 200項成功
- 400無效的輸入
- 401未經授權的存取
- 500內部伺服器錯誤

## 範例要求

### 新增至現有專案

```json
{
  "title": "Add to existing Project",
  "type": "addToExistingProject",
  "path": "/content/projects/test_project_1_existing",
  "translationDetails": {
    "map": {
      "id": "GUID-06527014-062d-46dc-8fea-48b4b4497c51-en"
    },
    "languages": ["de"],
    "versionDetails": {
      "versionSelector": "versionAsOfDate",
      "version": "2025-12-05T10:30:00+01:30"
    }
  },
  "filterDetails": [
    { "name": "referenceType", "values": [] },
    { "name": "fileType", "values": [] },
    { "name": "documentState", "values": [] },
    { "name": "translationStatus", "values": [] }
  ]
}
```

### 新增至具有基準線的現有專案

```json
{
  "title": "Add to existin project Project with baseline",
  "type": "addToExistingProject",
  "path": "/content/projects/existing_project_path",
  "translationDetails": {
    "map": {
      "id": "GUID-06527014-062d-46dc-8fea-48b4b4497c51-en"
    },
    "languages": ["de"],
    "versionDetails": {
      "versionSelector": "baseline",
      "version": "test1"
    }
  },
  "filterDetails": [
    { "name": "referenceType", "values": ["Direct"] },
    { "name": "fileType", "values": [] },
    { "name": "documentState", "values": [] },
    { "name": "translationStatus", "values": [] }
  ]
}
```

## 翻譯專案建立狀態

追蹤新建立翻譯專案之翻譯狀態的GET API。

## 請求 URL

`http://<aem-guides-server>:<port-number>/bin/guides/v1/translation/project/creationstatus`

## 請求類型

GET

## 要求引數

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `path` | 字串 | 專案路徑 |
| `languageStatusMap` | 字串 | 對於每種請求的語言，傳回完成狀態：進行中、已完成、失敗、已略過 |


## 請求範例

```json
{
  "path": "/content/projects/test_project_1_ondec5",
  "languageStatusMap": {
    "de": "Completed"
  }
}
```



