---
title: 設定 Dispatcher
description: 瞭解如何設定Dispatcher
feature: Installation
role: Admin
level: Experienced
source-git-commit: 834959a6a0e22cd5d2b2c5d0e57ceb6d45c0c666
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 7%

---

# 設定 Dispatcher {#id213BCM0M05U}

如果您打算在AEM Author例項上搭配使用Dispatcher以及AEM Guides，則您需要執行下列額外設定以完成設定：

>[!NOTE]
>
> Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。如需有關使用Dispatcher的詳細資訊，請參閱[Dispatcher概觀](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=en)。

## 在URL中啟用AllowEncodedSlases

在AEM Dispatcher設定中，預設不會啟用具有編碼斜線的URL，但是當您在AEM Guides中工作時，需要啟用此設定。 若要這麼做，您必須在Apache設定中將`AllowEncodedSlashes`引數設定為&#x200B;**On**，如下列程式碼片段所示：

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

執行以下步驟來更新`mime.types`檔案：

1. 使用SSH連線至Dispatcher伺服器並瀏覽至`httpd.conf`檔案。

1. 檢查`mime.types`檔案的路徑。

1. 開啟`mime.types`檔案並搜尋「 text/html」。 「text/html」的預設對應為：

   `text/html html htm`

1. 透過將ditamap和dita擴充功能新增為來更新對應：

   `text/html html htm ditamap dita`

1. 儲存並關閉檔案。


此設定更新會確保Dispatcher轉譯的DITA map和主題檔案在Assets UI中顯示為HTML。

## 允許使用者偏好設定請求URL

將Dispatcher與AEM Guides搭配使用時，如果您的編寫執行個體前端有Dispatcher，則進行下列兩項變更：

- 將POST要求URL加入白名單。 以下提供範例`/filters`規則：將此規則新增到Dispatcher設定檔：

```json
/xxxx {/type "allow" /method "POST" /url "/home/users/*/preferences"}
```

- 確定未在Author Dispatcher上快取URL模式`/libs/cq/security/userinfo.json`，因此請在`\(like below\)`中新增規則`author\_dispatcher.any`

```json
/xxxx {
                /glob "/libs/cq/security/userinfo.json"
                /type "deny"
                }
```

