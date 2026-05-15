---
title: Jui框架
description: 瞭解Jui框架
role: User, Admin
exl-id: c193cf90-5916-4d8c-88f1-be5014beca1c
TQID: https://experienceleague.adobe.com/AQFEy2bHTDHXq6QH8KTBOEzUvtA3Hf2ojhxvD0dsI7o
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: c6d09140-3c91-45d3-b7ed-b681af752f43id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 268
ht-degree: 1%

---

# Jui框架

在開始瞭解如何撰寫擴充功能之前，請先瞭解架構的結構。
以便我們有效地加以擴充。

## 簡介

JUI是MVC架構，以React和Adobe React Spectrum元件為基礎。 JUI是JSON使用者介面。 它包含多個Git存放庫。

JUI-Core是核心程式庫，具有將JSON設定轉換為工作react元件的所有邏輯，並將其與相關控制器類別例項連結。
JUI-React-Spectrum程式庫有Adobe React Spectrum元件的包裝函式Widget

## JUI核心設計

### MVC UI設計

![JUI MVC流程](./imgs/jui-mvc-flow.png)

### 小工具

- 具有唯一識別碼。
- 擁有個別JSON檔案以供檢視。
- 可以擁有自己的或共用的控制器。
- 可以使用父模型或新模型。
- 可以有UI元素（React元件）
- 可以有其他Widget
- 應用程式是Widget

![JUI Widget](./imgs/jui-widget.png)

### 元素

- 是HTML/React元件。
- 沒有任何模型，其使用父Widget模型。

### 事件處理常式

- 下一個(eventOpts)
   - 使用某些選項觸發事件
- 訂閱（回撥）
   - 取得設定引發的事件通知

### 應用程式/全域模型

- 下一個（新值）
   - 若要發佈新值
- 訂閱（回撥）
   - 若要取得值變更的通知
   - 首次取得舊值
- GetValue()
   - 取得目前值

### 控制器

- 應該從控制器類別延伸
- API
- 建立模型
   - 若要建立子Widget個別模型
- InitEventHandler
   - 若要建立子Widget個別事件處理常式
- RegisterCommand
   - 註冊本機、父系或應用程式事件
- 下一個(eventName， eventHandler)
   - 若要觸發子Widget事件處理常式、父Widget事件處理常式或應用程式事件處理常式的事件
- 訂閱(callback， eventHandler)
- SubscribeAppModel(callback)

### 範例應用程式設計

![範例應用程式](./imgs/jui-sample-app.png)
