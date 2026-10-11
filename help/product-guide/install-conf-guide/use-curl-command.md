---
title: 使用curl命令
description: 瞭解如何對Experience Manager Guides中的上傳內容使用curl命令。
feature: Migration
role: Admin
level: Experienced
exl-id: 7772246c-f885-46c0-a1e5-915d111bbc61
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: 5be0fc8f-1cff-5c3e-bb92-2903a56a3de6
    internal-label: Migration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%
---
# 使用curl命令

您也可以使用curl命令在DAM中建立資料夾、上傳檔案，以及在上傳的內容上新增中繼資料。

## 建立資料夾

執行以下命令，在AEM存放庫中建立資料夾：

```curl
curl --user <username>:<password> --data jcr:primaryType=sling:Folder "<server folder path>"
```

指定下列引數以建立資料夾：

- `<username>:<passowrd>`：指定要存取AEM存放庫的使用者名稱和密碼。 此使用者必須擁有資料夾建立許可權。

- `jcr:primaryType=sling:Folder`：指定此引數&#x200B;*為*，以建立資料夾型別資源。

- `<server folder path>`：完整的資料夾路徑，包括您要在AEM存放庫中建立的新資料夾名稱。 例如，如果您將路徑指定為`http://192.168.1.1:4502/content/dam/projects/AEM-Guides`，則會在DAM的`projects`資料夾中建立資料夾`AEM-Guides`。


## 上傳檔案

執行以下命令，在AEM存放庫中上傳檔案：

```curl
curl --user <username>:<password> -T "<local file path>" "<server folder path>"
```

指定下列引數以上傳檔案：

- `<username>:<passowrd>`：指定要存取AEM存放庫的使用者名稱和密碼。 此使用者必須擁有`server folder path`的寫入許可權。

- ``local file path``：您想要上傳之本機系統上的完整檔案路徑。

- `<server folder path>`：您要上傳檔案的AEM伺服器上的完整資料夾路徑。


## 新增後設資料

執行以下命令，在檔案中新增中繼資料：

```curl
curl --user <username>:<password> -F<attribute name>=<value> <metadata node path>
```

指定下列引數以新增中繼資料資訊：

- `<username>:<passowrd>`：指定要存取AEM存放庫的使用者名稱和密碼。 此使用者必須擁有``metadata node path``的寫入許可權。

- ``-F<attribute name>=<value>``： `<attribute name>`是中繼資料屬性的名稱，例如`audience`，而`<value>`可以是`internal`。 您可以指定多個以空格分隔的屬性名稱 — 值組。

- `<metadata node path>`：完整的資料夾路徑，包括檔案名稱及其中繼資料節點。 例如，如果您將路徑指定為`http://192.168.1.1:4502/content/dam/projects/AEM-Guides/intro.xml/jcr:content/metadata`，則指定的中繼資料資訊會設定在`intro.xml`檔案上。
