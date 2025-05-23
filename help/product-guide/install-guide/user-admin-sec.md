---
title: 使用者管理與安全性
description: 瞭解使用者管理與安全性的運作方式
exl-id: 1269a652-5261-413d-9ea0-b4f75003e9d8
feature: User Management
role: Admin
level: Experienced
source-git-commit: 9b657b0530db8fafe3bb6d30a9002791acf8f226
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 9%

---

# 使用者管理與安全性 {#id181AED00G5Z}

若要在AEM Guides中存取及設定功能，您必須建立使用者。 接著，這些使用者就可以獲得許可權，以存取AEM Guides中的所有或特定功能。 瞭解如何設定和維護使用者授權，同時也瞭解在AEM中驗證和授權如何運作背後的理論。

AEM檔案中的下列主題將幫助您瞭解使用者管理與安全性相關的概念和功能：

- 在AEM中[使用者和群組](https://helpx.adobe.com/tw/experience-manager/6-5/sites/administering/using/security.html#UsersandGroupsinAEM)

- AEM中的[許可權](https://helpx.adobe.com/tw/experience-manager/6-5/sites/administering/using/security.html#PermissionsinAEM)

- [管理使用者和群組](https://helpx.adobe.com/tw/experience-manager/6-5/sites/administering/using/security.html#ManagingUsersandGroups)

- [管理許可權](https://helpx.adobe.com/tw/experience-manager/6-5/sites/administering/using/security.html#ManagingPermissions)


## AEM Guides建立的使用者群組 {#id181TF0K0MHT}

AEM Guides提供三個現成可用的群組。 這些群組是： *作者*、*檢閱者*&#x200B;和&#x200B;*發佈者*。 根據使用者相關聯的群組，允許他們執行特定工作。 例如，發佈工作只能由發佈者執行，不能由作者或稽核者執行。 同樣地，作者可以建立新主題，而稽核者只能稽核主題。

>[!TIP]
>
> 如需設定使用者許可權的最佳實務，請參閱「最佳實作指南」中的&#x200B;*許可權*&#x200B;區段。

下表列出各種工作以及可執行這些工作的群組：

| 任務 | 作者 | 檢閱者 | 發佈者 |
|----|-------|---------|----------|
| 建立DITA主題 | 是 |   | 是 |
| 建立DITA Map | 是 |   | 是 |
| 對應集合 | 是 |   | 是 |
| 建立評論任務 | 是 |   | 是 |
| 檢閱主題[1](#fntarg_1) | 是 | 是 | 是 |
| 關鍵解析度 | 是 |   | 是 |
| 在FrameMaker中開啟 | 是 |   | 是 |
| 簽出/簽入 | 是 |   | 是 |
| 編輯主題 | 是 |   | 是 |
| 移動主題 | 是 |   | 是 |
| 編輯主題屬性 | 是 |   | 是 |
| 複製 | 是 |   | 是 |
| 刪除 | 是 |   | 是 |
| 共用 | 是 |   | 是 |
| **檔案狀態** |
| 建立/編輯檔案狀態設定檔 |   |   | 是 |
| 變更檔案狀態[2](#fntarg_2) | 是 | 是 | 是 |
| **DITA map主控台中可用的功能\（輸出預設集索引標籤\）** |
| 產生 |   |   | 是 |
| 編輯 |   |   | 是 |
| 重複項目 |   |   | 是 |
| 建立 |   |   | 是 |
| 刪除預設集 |   |   | 是 |
| **DITA map主控台中可用的功能\（輸出標籤\）** |
| 檢視產生的輸出 | 是 |   | 是 |
| **DITA map主控台中可用的功能\（主題標籤\）** |
| 建立評論任務 | 是 |   | 是 |
| 編輯 | 是 |   | 是 |
| **DITA map主控台中可用的功能\（基準線標籤\）** |
| 建立 |   |   | 是 |
| 編輯 |   |   | 是 |
| 重複項目 |   |   | 是 |
| 移除 |   |   | 是 |
| DITA map主控台\（報表標籤\） | 是 |   | 是 |
| DITA map主控台中可用的&#x200B;**功能\（條件預設集\）** |
| 建立/編輯條件預設集 |   |   | 是 |

## 使用者群組的其他附註

下列清單包含一些與使用者群組及對應許可權相關的建議和點：

- 如果您希望使用者開始翻譯或檢閱工作流程，請確定使用者是&#x200B;*Publishers*&#x200B;與&#x200B;*projects-administrators群組*&#x200B;的成員。

- 使用者必須在他們需要的來源和目標語言資料夾中，擁有讀取、建立、刪除和修改許可權。

- 如果您建立專案，則您是具有&#x200B;*Publishers*&#x200B;許可權之專案的所有者。 若要讓專案中的其他使用者能夠檢視其團隊成員、建立任務或建立工作流程，他們必須在`/home/users`和`/home/groups`節點上擁有讀取存取權。 授予`/home/users`和`/home/groups`節點讀取存取權的一種方式是授予`projects-users`群組的讀取存取權。

- *檢閱者*&#x200B;可以從[專案]主控台或收件匣通知連結，存取及新增檢閱中主題的檢閱註解。 此外，此存取權僅在稽核任務開啟時可用。

- 根據預設，*發佈者*&#x200B;在DAM中擁有下列資料夾的存取權和許可權：

   - ``/var/dxml``-\>讀取和寫入

   - `/content/dam/fmdita-outputs` -\>讀取和寫入

   - `/content/output/sites` -\>讀取和寫入

  如果您使用上述預設發佈位置以外的任何其他位置，則必須向您的發佈者授予明確的讀取和寫入許可權。

- *作者*、*檢閱者*&#x200B;和&#x200B;*發佈者*&#x200B;群組下的所有使用者都擁有DAM中所有內容的讀取存取權。

- 檔案夾層級許可權必須透過使用者管理頁面指派給使用者。

- 如果您希望您的使用者能夠在DAM上執行搜尋作業，則讓您的使用者成為&#x200B;*dam-users*&#x200B;群組的成員。

- 如果您想要將管理員許可權授予任何使用者，您可以透過AEM標準群組(例如&#x200B;*管理員*、*專案管理員*&#x200B;或OSGI設定\（Felix主控台\）)授予他們存取權，以執行此操作。

- 若要授予使用者變更檔案狀態的許可權，請確定您在檔案狀態設定檔的狀態轉變區段中新增使用者。

[1](#fnsrc_1)如果邀請&#x200B;*作者*&#x200B;與&#x200B;*發行者*&#x200B;檢閱。[2](#fnsrc_2)根據檔案狀態設定檔中授予使用者的許可權。
