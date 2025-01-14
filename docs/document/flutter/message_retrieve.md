# 从服务器获取会话和消息（消息漫游）

<Toc />

本文介绍用户如何从消息服务器获取会话和消息，该功能也称为消息漫游，指即时通讯服务将用户的历史消息保存在消息服务器上，用户即使切换终端设备，也能从服务器获取到单聊、群聊的历史消息，保持一致的会话场景。

## 实现原理

使用环信即时通讯 IM Flutter SDK 可以通过 `EMChatManager` 类的以下方法从服务器获取历史消息：

- `getConversationsFromServer` 获取服务器保存的会话列表；
- `fetchHistoryMessages` 获取服务器保存的指定会话中的消息。

## 前提条件

开始前，请确保满足以下条件：

- 完成 SDK 初始化，并连接到服务器，详见 [快速开始](quickstart.html)。
- 了解环信即时通讯 IM API 的使用限制，详见 [使用限制](/product/limitation.html)。

## 实现方法

### 从服务器获取会话

该功能需联系商务开通，开通后，用户默认可拉取 7 天内的 10 个会话（每个会话包含最新一条历史消息）。如需调整会话数量或时间限制，请联系商务。

调用 `getConversationsFromServer` 从服务端获取会话。我们建议在 app 安装时或本地没有会话时，调用该 API。否则调用 `loadAllConversations` 即可。示例代码如下：

```dart
try {
  List<EMConversation> list =
      await EMClient.getInstance.chatManager.getConversationsFromServer();
} on EMError catch (e) {
}
```

### 分页获取指定会话的历史消息

你还可以从服务器分页获取指定会话的历史消息，实现消息漫游功能。为确保数据可靠，我们建议你多次调用该方法，且每次获取的消息数小于 50 条。获取到数据后，SDK 会自动将消息更新到本地数据库。

```dart
try {
  // 会话 ID
  String convId = "convId";
  // 会话类型。详见 `EMConversationType` 枚举类型。
  EMConversationType convType = EMConversationType.Chat;
  // 获取的最大消息数
  int pageSize = 10;
  // 搜索的起始消息 ID
  String startMsgId = "";
  EMCursorResult<EMMessage?> cursor =
      await EMClient.getInstance.chatManager.fetchHistoryMessages(
    conversationId: convId,
    type: convType,
    pageSize: pageSize,
    startMsgId: startMsgId,
  );
} on EMError catch (e) {
}
```
