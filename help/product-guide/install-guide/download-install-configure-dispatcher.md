---
title: 設定Dispatcher
description: 瞭解如何設定Dispatcher
exl-id: 525de1c3-5a79-4d65-89b4-ca05ae660c2c
feature: Installation
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 5%

---

# 設定Dispatcher {#id213BCM0M05U}

如果您打算在AEM Author執行個體上搭配使用Dispatcher以及AEM Guides，則您需要執行下列額外設定以完成設定：

>[!NOTE]
>
> Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。如需有關使用Dispatcher的詳細資訊，請參閱[Dispatcher概觀](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=en)。

## 在URL中啟用AllowEncodedSlases

AEM Dispatcher設定中預設不會啟用具有編碼斜線的URL，但在AEM Guides中運作時，您需要啟用此設定。 為此，您需要在Apache設定中將AllowEncodedSlashes引數設定為On ，如下列程式碼片段所示：

```XML
<VirtualHost *:80>
                ServerName www.geometrixx-outdoors.com
                **AllowEncodedSlashes On**
                <Directory />
                <IfModule disp_apache2.c>
                SetHandler dispatcher-handler
                </IfModule>
                Options FollowSymLinks
                AllowOverride None
                </Directory>
                </VirtualHost>
            
```

## 設定DITA的mime.types檔案

搭配AEM Guides使用Dispatcher時，您必須確保DITA map和主題檔案呈現為HTML，讓作者如預期般檢視內容\（而非原始文字格式\）。

執行以下步驟來更新mime.types檔案：

1. 使用SSH連線至Dispatcher伺服器並瀏覽至httpd.conf檔案。

1. 檢查「 mime.types」檔案的路徑。

1. 開啟mime.types檔案並搜尋「text/html」。 「text/html」的預設對應為：

   `text/html html htm`

1. 透過將ditamap和dita擴充功能新增為來更新對應：

   `text/html html htm ditamap dita`

1. 儲存並關閉檔案。


此設定更新可確保Dispatcher轉譯的DITA map和主題檔案在Assets UI中顯示為HTML。

## 允許使用者偏好設定請求URL

將Dispatcher與AEM Guides搭配使用時，如果您的編寫執行個體前端有Dispatcher，則進行下列兩項變更：

- 將POST請求URL加入白名單。 以下提供&quot; `/filters`&quot;規則的範例 — 將此規則新增到Dispatcher設定檔案：

```json
/xxxx {/type "allow" /method "POST" /url "/home/users/*/preferences"}
```

- 確保Author Dispatcher上未快取URL模式「 /libs/cq/security/userinfo.json」，因此請在author\_dispatcher.any中新增規則\（如下所示\）

```json
/xxxx {
                /glob "/libs/cq/security/userinfo.json"
                /type "deny"
                }
```

**上層主題：**[&#x200B;下載並安裝](download-install.md)
