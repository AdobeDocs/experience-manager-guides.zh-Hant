---
title: Jui框架
description: 瞭解Jui框架
role: User, Admin
exl-id: c193cf90-5916-4d8c-88f1-be5014beca1c
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# Jui框架

在開始瞭解如何撰寫擴充功能之前，請先瞭解架構的結構。
以便我們有效地加以擴充。

## 簡介

JUI是MVC架構，以React和AdobeReact Spectrum元件為基礎。 JUI是JSON使用者介面。 它包含多個Git存放庫。

JUI-Core是核心程式庫，具有將JSON設定轉換為工作react元件的所有邏輯，並將其與相關控制器類別例項連結。
JUI-React-Spectrum  程式庫有AdobeReact Spectrum元件的包裝函式小工具

## JUI核心設計

### MVC UI設計

![JUI MVC流程](./imgs/jui-mvc-flow.png)

### Widget

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
