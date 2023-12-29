# 消息扩展特性 

<Toc />

除了在聊天室中发送和查看消息，还可以长按一条消息进行消息举报、翻译、撤回和禁言成员。

## 消息举报

在聊天室中，当用户发现其他人发布了可能违反聊天室规则或道德准则的消息时，可以举报该消息，促使聊天室所有者采取适当的行动。

在 UIKit 中，默认通过长按单条消息，触发举报选项，实现消息举报。用户可以选择举报原因，如色情内容、恶意攻击、仇恨言论、垃圾广告等。你也可以根据业务需要，修改举报原因选项。

![img](@static/images/uikit/chatroomfeature/msg_report.png =600x400)

## 消息翻译

将聊天室中的单条消息从一种语言转换成另一种语言。翻译特性可以帮助聊天室中的成员克服语言障碍，促进跨语言沟通和交流。

在 UIKit 中，默认通过长按单条消息，触发翻译选项，实现消息翻译。默认翻译后的语言与用户设备的系统设置保持一致，例如，若你的手机系统语言为中文，则消息翻译的目标语言也是中文。翻译后的消息显示在原消息的位置，替换原消息。

![img](@static/images/uikit/chatroomfeature/msg_translate.png =500x500)

## 消息撤回

在聊天室中撤销已经发送的消息。当用户发送一条消息后，可能会发现消息内容有误或不妥当，可以使用消息撤回功能将消息从聊天室的聊天窗口中删除，使其他用户无法再看到该消息。在 UIKit 中，默认通过长按单条消息，触发撤回选项，实现对该条消息的撤回。撤回的默认限制是 2 分钟，超时则无法撤回。时间限制可[通过环信控制台的进行调整](/product/enable_and_configure_IM.html#设置消息撤回-rest-客户端)，最长为 7 天。

:::tip
所有用户只能撤回自己发送的消息，即使聊天室所有者也不能撤回其他成员发送的消息。
:::

![img](@static/images/uikit/chatroomfeature/msg_recall.png =800x600)

## 禁言成员

在聊天室中对指定成员采取禁止发言的措施。禁言通常是对违反聊天室规则、发表不当言论或不断干扰聊天室秩序的成员所采取的一种惩罚。

在 UIKit 中，默认通过长按单条消息，触发禁言选项，实现对发送该条消息的成员的禁言惩罚。此外，用户也可以通过[成员列表](roomfeature_member#查看成员列表)对指定成员直接进行禁言惩罚。

当成员被禁言后，将会被加入[已禁言列表](roomfeature_common#已禁言列表)。如果用户想要取消禁言成员，需要在已禁言列表中找到该成员，点击成员右端的管理功能按钮，触发解除禁言选项，实现取消禁言的操作。

![img](@static/images/uikit/chatroomfeature/msg_mute.png =500x500)