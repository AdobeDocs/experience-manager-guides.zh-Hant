---
title: REST API可註冊資料來源聯結器
description: 瞭解REST API以註冊資料來源聯結器
exl-id: e2811892-c3cf-41f5-94d8-c2b37823a53a
feature: Rest API Data Source
role: Developer
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# REST API可註冊資料來源聯結器 {#id236LG0Y0CXA}

下列REST API可讓您註冊資料來源聯結器。

## 註冊資料來源聯結器

註冊資料來源聯結器的GET方法。

**請求URL**：
`http://server:port/bin/guides/v1/konnect/config/register?path=<uploaded file path>`

**引數**： |名稱|型別|必要|說明| --------------------------- |`path`|字串|是|指向AEM存放庫中路徑的字串。 它可以是 `/content/dam or /var/dxml`.|

**範例**：\
`http://host:4502/bin/guides/v1/konnect/config/register?path=/var/dxml/konnect/jira.json`
