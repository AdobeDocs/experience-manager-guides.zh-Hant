---
title: 自訂
description: 自訂稽核應用程式
role: User, Admin
exl-id: 9f6a4e9f-fc13-40b5-a30f-151c94faff81
source-git-commit: 4f00d6b7ad45636618bafe92e643b3e288ec2643
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# 自訂稽核應用程式

為了方便自訂檢閱應用程式，我們提供了一些鉤點，詳見以下說明：

## Review-Comment

- 識別碼： `review_comment`
- 勾點： `this.updateExtraProps`：

如同[這裡](../../aem_guides_framework/basic-customisation.md)所述，自訂期間新增的任何新屬性都會落在`this.model.extraProps`之下。 方法`updateExtraProps`可讓您新增屬性到檢閱註解，同時處理伺服器上新增屬性的更新及儲存。

### 使用範例

例如，您想要新增欄位`commentRationale`和`severity`至您的註解。
讓我們將`commentRationale`更新為「這是一個重要句子」。 和`severity`設為「嚴重」。
您可以使用語法來達成此目的：

```typescript
  this.next('updateExtraProps', {
    'commentRationale': 'This is an important sentence.',
    'severity': 'CRITICAL'
  })
```

上述程式碼片段會處理值的更新及儲存。 可藉由定義檢視在UI上呈現儲存的值。

```JSON
{
    "component" : "label",
    "label": "@extraProps.commentRationale"
}
```

## 內嵌稽核面板

- 識別碼： `inline_review_panel`

1. 勾點： `onNewCommentEvent`
勾點`onNewCommentEvent`可讓您在新的註解或回覆事件上擲回事件或呼叫方法。
在`onNewCommentEvent`中收到的引數包括：
   - 事件：已傳送的評論/回覆事件。
   - newComment：布林值
如果傳送的事件是新的註解事件，即`highlight`、`insertion`、`deletion`、`sticky note comment`
   - newReply：布林值
如果傳送的事件是新的回覆事件。

2. 勾點： `sendExtraProps`

如果您想要延伸`event`並從內嵌稽核面板傳送`extraProps`，此掛接將有所助益。 我們將在下方說明這兩個鉤點的用途。

### 內嵌稽核面板範例

假設我們每次傳送新評論或回覆時都要傳送額外的Prop `userInfo`。 現在，這將透過內嵌稽核面板完成，但我們沒有新產生註解的commentId參考，因此為了實現這一點，我們可以編寫以下程式碼。

```typescript
    onNewCommentEvent(args){
      const events = _.get(args, "events")
      const currTopicIndex = tcx.model.getValue(tcx.model.KEYS.REVIEW_CURR_TOPIC) || this.getValue('currTopicIndex') || "0"
      const event = _.get(_.get(events, currTopicIndex), '0')
      const newComment = _.get(args, 'newComment')
      const newReply = _.get(args, 'newReply')
      if ((newComment || newReply) && event) {
        this.next('setUserInfo', event)
      }
    },
```

在上述程式碼片段中，我們正在檢查已傳送事件是否為新註解或回覆。 若有新的註解或回覆，我們正在呼叫方法`setUserInfo`

```typescript
    setUserInfo(event) {
      this.loader?.getUserInfo(event.user).subscribe(userData => {
        const extraProps = {
          "userFirstName": userData?.givenName || '',
          "userLastName": userData?.familyName || '',
          "userTitle": userData?.title || '',
          "userJobTitle": userData?.jobTitle || '',
          'userEmail': userData?.email || '',
        }
        const data = {... event, extraProps}
        this.next(
          'sendExtraProps',
          data
        )
      })
    },
```

在上述方法中，我們將擴充事件以傳送extraProp，包括使用者的名字、電子郵件、標題等。 以此方式擴充事件可確保以正確的commentId傳送extraProp，確保將其附加到正確的註解。

掛接`updateExtraProps`本身會呼叫掛接`sendExtraProps`，所以何時該使用什麼？

我們在`review_comment`控制器中使用`updateExtraProps`，該控制器已經有註解的`id`，因此您只需要提及`extraProps.`

`inline_review_panel`無法存取註解的ID，因此每當您需要從內嵌稽核面板傳送事件時，`sendExtraProps`都會派上用場。
