[SOCIAL](../groups/SOCIAL.SOCIAL.md) / ChatService

# ChatService <Badge type="tip" text="Class" /> <Score text="ChatService" />

**`Instance`**

是一个用于实现聊天功能的类，它可以管理用户之间的交流并提供相关的服务。

## Table of contents

| Methods |
| :-----|
| **[asyncBroadcastMessage](Service.ChatService.md#asyncbroadcastmessage)**(`type`: [`MessageType`](../enums/Service.MessageType.md), `content`: `string`): `Promise`<[`BroadcastMessageResult`](../modules/Service.Service.md#broadcastmessageresult)\> <br> 发送富文本消息到聊天窗口中。|
| **[getInstance](Service.ChatService.md#getinstance)**(): [`ChatService`](Service.ChatService.md) <br> 获取API实例进行调用|

## Methods

### asyncBroadcastMessage <Score text="asyncBroadcastMessage" /> 

• **asyncBroadcastMessage**(`type`, `content`): `Promise`<[`BroadcastMessageResult`](../modules/Service.Service.md#broadcastmessageresult)\> <Badge type="tip" text="server" />

发送富文本消息到聊天窗口中。
禁止在回调中调用该接口。限制每个ds消息发送从第一个消息发送开始计时60秒内最多发送60条消息。定时器清空计数后下一次发送消息再次开始计数。需要用到富文本格式，富文本全部功能请查看产品手册。


使用示例:创建一个名为"messageExample"的脚本，放置在对象管理器中，打开脚本，输入以下代码保存，运行游戏，你将在场景中看到在聊天框中显示富文本字体的效果。代码如下：
```ts
@Core.Class
 export default class messageExample extends Core.Script {

     protected onStart(): void {
          this.Mgs();
     }

     @Core.Function(Core.Server)
     public Mgs(){
         let type: MessageType.Room;
         // content内容可以是富文本格式文字。
         // 富文本可使文本实现不同字号、不同颜色等多种效果。
         // <b>以粗体显示文本。eg:We are <b>not</b> amused. =>not字体为粗体
         // <color=#ff0000ff>或<color=#red>根据参数值#rrggbbaa设置文本的颜色，分别表示颜色的红、绿、蓝和 Alpha（透明度）值，大小写都能识别.eg:We are <color=#red>colorfully</color> amused. =>colorfully字体为红色。
         // <u>以下划线显示文本。eg:We are <u>not</u> amused. =>not字体存在下划线。
         let content = "<b><color=#ff0000ff>系统提示：</color></b>恭喜玩家<b><u><color=#yellow>起个名字好难</color> </u></b>！在<u><color=#red>萌宠转转转</color></u>活动中获得活泼可爱的<u><color=#black>萌兔宝宝</color> </u> ！";
         ChatService.getInstance().asyncBroadcastMessage(type,content);
      }
 }

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `type` | [`MessageType`](../enums/Service.MessageType.md) | 发送消息类型 |
| `content` | `string` | 消息内容 |

#### Returns

`Promise`<[`BroadcastMessageResult`](../modules/Service.Service.md#broadcastmessageresult)\>

发送消息的结果

___

### getInstance <Score text="getInstance" /> 

• `Static` **getInstance**(): [`ChatService`](Service.ChatService.md) 

获取API实例进行调用


::: warning Precautions

只在由233拉起生效

:::

#### Returns

[`ChatService`](Service.ChatService.md)

返回API实例用以调用相关功能函数
