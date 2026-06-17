---
title: SCORM預設集設定
description: 瞭解產品培訓和學習中的各種SCORM預設集設定
feature: Authoring
role: User
exl-id: b3000708-6120-4725-bea1-0b8e58048948
TQID: https://experienceleague.adobe.com/9WSwgksrX0fahrniOalbizWFXCqcW0QlGAHn707vm-k
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: f7c0b10f032c2584fb6e951da898faaeb4ca7aaf
workflow-type: tm+mt
source-wordcount: 331
ht-degree: 0%

---

# 設定SCORM輸出預設集

建立預設集後，請配置SCORM預設集設定。 預設集組態選項會整理在「一般」、「內容」和「發佈」標籤下。

- **一般：**&#x200B;用於指定基本輸出設定，例如支援的版本、輸出路徑、ZIP檔案名稱、輸出範本，以及與學習者體驗相關的其他選項。

  ![](assets/scorm-general-tab-v3.png){width="650"}

  **學習者的體驗**

   - **學習者必須依循序進行內容**：確保學習者能依固定順序進行測驗，且不能略過或跳到問題之間。
   - **學習者必須嘗試所有問題才能繼續**：要求學習者先嘗試所有問題，才能提交測驗，以防止提交不完整的試卷。
   - **隨機排列每次嘗試的問題順序**：以不同的順序顯示每次嘗試的測驗問題，有助於降低可預測性。
   - **隨機選擇每個嘗試的答案**：隨機選擇每個嘗試的答案選項，減少根據位置猜測的機會。
   - **在測驗報告中使用問題識別碼**：在測驗報告中包含唯一的問題識別碼，以便更輕鬆地追蹤、分析並將結果對應回特定問題。
   - **產生後工作流程**：選擇此選項時，會顯示新的「產生後工作流程」下拉式清單，其中包含所有已設定的工作流程。

- **內容：**&#x200B;使用指定可用的條件篩選（使用DITAVAL或使用某些條件預設集）和變數集。

  ![](assets/scorm-content-tab.png){width="650"}


- **發佈至LMS：**&#x200B;使用此設定直接將您的內容發佈至Adobe Learning Manager (ALM)。 從&#x200B;**發佈伺服器**&#x200B;下拉式清單中，選取&#x200B;**Adobe Learning Manager**，然後選擇先前在Workspace設定中設定的必要&#x200B;**發佈設定檔**。 選取的設定檔可用來建立連線，並將產生的內容上傳至ALM。

  >[!NOTE]
  >
  > 將內容發佈至ALM之前，您必須先設定Adobe Learning Manager發佈設定檔。 如需詳細資訊，請檢視[發佈設定檔](../lc-config-guide/lc-folder-profile.md)。

  ![](assets/scorm-publish-lms.png){width="650"}

設定好所有變更後，請使用SCORM預設集頁面工具列右角的&#x200B;**儲存**，儲存SCORM預設集的變更。
