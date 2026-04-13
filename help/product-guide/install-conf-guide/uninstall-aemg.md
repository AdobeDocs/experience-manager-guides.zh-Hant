---
title: 解除安裝AEM Guides
description: 瞭解如何解除安裝AEM Guides
feature: Installation
role: Admin
level: Experienced
exl-id: 84b248da-af7b-4811-a184-4ab17838faaa
source-git-commit: 2749c0df3bd5640c9491dce3ab6c96f707625969
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# 解除安裝內部部署適用的AEM Guides{#id21BHG0C0SXA}

您可以使用AEM Guides Package Manager解除安裝CRX for On-Premise。 在解除安裝期間，存放庫的內容會還原成安裝套件之前立即建立的快照。

執行以下步驟來解除安裝內部部署適用的AEM Guides：

1. 登入您的AEM執行個體，並導覽至CRX封裝管理員。 存取封裝管理器的預設URL為：

   ```http
   http://<server name>:<port>/crx/packmgr/index.jsp
   ```

1. 搜尋`com.adobe.fmdita`封裝。
1. 按一下封裝以展開它。
1. 按一下&#x200B;**更多**&#x200B;以開啟下拉式清單。
1. 按一下&#x200B;**解除安裝**，然後等待解除安裝完成。
1. 如果您不再需要此封裝，請在解除安裝封裝後按一下&#x200B;**刪除**。

## 解除安裝之後

若要在解除安裝後清除剩餘檔案，請執行下列步驟：

1. 使用以下專案清除指令碼快取：

   ```http
   http://<host>:<port>/system/console/scriptcache
   ```

1. 您可以使用以下工具讓快取失效：

   ```http
   http://<host>:<port>/libs/granite/ui/content/dumplibs.rebuild.html?back=true
   ```

1. 按一下&#x200B;**讓快取失效**。
1. 清除瀏覽器的快取。
