---
title: 擴充功能存放庫簡介
description: AEM Guides擴充功能套件目錄結構
role: User, Admin
exl-id: 99a00b3e-a5c9-41d8-a73d-8690d587277e
TQID: https://experienceleague.adobe.com/REfq-LVYahMiO0avNtO7aOsXeJvkC9Eqo0stpiX1Qgc
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 110
ht-degree: 0%

---

# AEM Guides擴充功能套件目錄結構

```text
├── src
│   ├── **/*{js,ts}
│   ├── index.ts
├── dist
│   ├── guides-extension.js
│   ├── guides-extension.umd.cjs
│   ├── build.css
├── node_modules
├── package.json
├── package-lock.json 
└── .gitignore
└── buildCSS.mjs // for creating tailwind classes
└── vite.config.js // config for specifying TS and javascript build options
└── taliwind.config.js // config for tailwind we can add custom config for a design system here
├── jsons // jsons for the aem app
│   ├── context_menus // jsons for the context menus
│   ├── review_app // jsons for the review app
│   ├── xmleditor // jsons for xmleditor
```

## /src

```text
├── src
│   ├── **/*{js,ts}
│   ├── index.ts
```

來源目錄將包含您擴充功能的typescript或javascript檔案。 index.ts檔案是擴充功能的進入點。 您可以在此處匯入所有元件，並將它們匯出為單一物件。 擴充功能會使用此物件來轉譯元件。

### /dist

這是最終組建目錄。 此檔案包含需要複製到AEM的最終JS和CSS

```test
├── dist
│   ├── gudies-extension.js // you can either choose es module (this one) or .cjs(other one) file
│   ├── gudies-extension.umd.cjs
│   ├── build.css // this is your tailwind css output
```

## /jsons

此目錄包含各種檢視的JSON。 您可以使用這些JSON來識別目標及自訂檢視。

```text
├── jsons // jsons for the aem app
│   ├── context_menus // jsons for the context menus
│   ├── review_app // jsons for the review app
│   ├── xmleditor // jsons for xmleditor
```
