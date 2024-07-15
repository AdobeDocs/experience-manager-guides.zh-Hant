---
title: 自訂應用程式
description: 自訂應用程式
role: User, Admin
exl-id: 3e454c48-2168-41a5-bbab-05c8a5b5aeb1
source-git-commit: 4f00d6b7ad45636618bafe92e643b3e288ec2643
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# 自訂應用程式

我們的應用程式採用MVC （模型、檢視、控制器）結構

## 模型

模型會定義各種屬性並儲存其值。 可使用語法從控制器存取儲存在模型中的各種屬性的值

```typescript
this.getValue('attributeName')
```

為了在應用程式中進行自訂，所有新建立的屬性都會新增到模型中的對應下。
若要在模型中設定新屬性，我們將在控制器中使用下列語法：

```typescript
// If a key is not already in model then it will be added to extraProps
this.setValue('key', value)
```

若要存取新增至模型的屬性，我們將使用下列語法：

```typescript
const value = this.getValue("key")
```

## 檢視

此檢視會定義應用程式的UI。 我們使用JSON檔案來定義檔案的檢視。 在此，我們會定義元件和css （如元件外部範例中所提供），並轉譯儲存在模型中的值。
在我們的應用程式中，每個檢視都是使用JSON來定義。 JSON是使用稱為`id`的唯一ID來參照。

## 控制器

控制器是用來處理事件及處理資料。 控制器是用來從伺服器擷取及傳送資料，是UI上顯示與儲存在後端之間的介面。

- 若要在初始化時設定值，請使用`init`函式。
- 若要將方法新增至控制器，請使用下列語法：

```typescript
methodName: function(args){
    // functionality
}
```

這裡的`methodName`用作`key`，參考JSON （檢視）或其他函式中的方法

- 若要呼叫控制器中的方法，請使用語法

```typescript
this.next('methodName', args)
```

## 範例

現在，讓我們以簡單範例說明這3個元件如何彼此互動。
我們將新增一個按鈕，可在點按時切換其標籤值

### 檢視範例

我們在下方定義按鈕的JSON，該按鈕會以變數名稱`buttonLabel`顯示儲存在模型中的動態文字。
在此範例中，按一下按鈕會變更其標籤。

```JSON
{
    "component": "button",
    "label": "@extraProps.buttonLabel",
    "variant": "cta",
    "on-click": "switchButtonLabel",
}
```

### 模型範例

在此情況下，`extraProps.buttonLabel`會保留按鈕的標籤

### 控制器範例

```typescript
  controller: {
    init: function (context) {
      context.setValue("buttonLabel", "Submit")
    },

    switchButtonLabel(){
        const buttonLabel = this.getValue("buttonLabel") === "Submit"? "Cancel" : "Submit"
        this.setValue("buttonLabel", buttonLabel)
    }
  }
```

以下GIF顯示上述程式碼的實際運作中
![basic_customization](imgs/basic_customisation.gif "基本自訂按鈕")
