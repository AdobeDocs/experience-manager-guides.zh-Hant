---
title: 設定覆寫
description: 瞭解如何設定覆寫
exl-id: dc5f81f7-5b0a-4d12-a944-ba66b0239d5c
feature: Installation
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# 設定覆寫 {#id216IFC003XA}

要進行任何設定更新，應使用以下通用方法：

1. 存取您的Cloud Manager的Git存放庫。

1. 在下列位置建立新的JSON檔案：

   src/main/content/jcr\_root/apps/fmditaCustom/config/

1. 以下列格式命名檔案：

   $\{PID\}.cfg.json

   在此，PID是設定的處理序ID。

1. 使用以下格式在JSON檔案中新增屬性：

   ```
   {
      "aem.adminuname": "updatedUserjson",
      "valid.characters": "[-a-zA-Z0-9_@$]",
      "dita.serialization": true
   }
   ```

1. 認可變更並執行Cloud Manager管道以部署更新的設定。


**父級主題：**[&#x200B;下載並安裝](download-install.md)
