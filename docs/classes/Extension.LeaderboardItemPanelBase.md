[UTILITY](../groups/UTILITY.UTILITY.md) / LeaderboardItemPanelBase

# LeaderboardItemPanelBase<T\> <Badge type="tip" text="Class" /> <Score text="LeaderboardItemPanelBase<T\>" />

排行榜主界面中的子UI，用来显示一条记录

## Type parameters

| Name | Type |
| :------ | :------ |
| `T` | extends [`IItemView`](../interfaces/Extension.IItemView.md) |

## Hierarchy

- [`BasePanel`](Extension.BasePanel.md)<`T`\>

  ↳ **`LeaderboardItemPanelBase`**

## Table of contents

| Accessors |
| :-----|
| **[playerId](Extension.LeaderboardItemPanelBase.md#playerid)**(): `number` <br> 当前显示对象的playerId|


::: details 点击查看继承
| Accessors |
| :-----|
| **[size](Extension.BasePanel.md#size)**(): [`Vector2`](Type.Vector2.md) <br> 面板尺寸|
| **[view](Extension.BasePanel.md#view)**(): `T` <br> 面板所控制的界面|
:::


| Methods |
| :-----|
| **[onAddToCanvas](Extension.LeaderboardItemPanelBase.md#onaddtocanvas)**(`playerId`: `number`, `rankIndex`: `number`): `void` <br> 显示在画布上调用，需要请复写|
| **[onFieldSet](Extension.LeaderboardItemPanelBase.md#onfieldset)**(`playerId`: `number`, `rankIndex`: `number`, `fieldId`: `number`, `fieldValue`: `string` \, `textBlockIndex`: `number`, `textBlock`: [`TextBlock`](UI.TextBlock.md)): `void` <br> 设置字段内容后调用，需要请复写|


::: details 点击查看继承
| Methods |
| :-----|
| **[onAdded](Extension.BasePanel.md#onadded)**(): `void` <br> 生命周期-被添加到父节点时候触发，可能会多次调用|
| **[onAwake](Extension.BasePanel.md#onawake)**(): `void` <br> 生命周期方法-构建面板自动触发，只会调用一次|
:::


### playerId <Score text="playerId" /> 

• `Protected` `get` **playerId**(): `number` <Badge type="tip" text="client" />

当前显示对象的playerId


#### Returns

`number`


## Methods
___

### onAddToCanvas <Score text="onAddToCanvas" /> 

• `Protected` **onAddToCanvas**(`playerId`, `rankIndex`): `void` <Badge type="tip" text="client" />

显示在画布上调用，需要请复写


#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `playerId` | `number` |  玩家id |
| `rankIndex` | `number` |  排名(0开始) |


___

### onFieldSet <Score text="onFieldSet" /> 

• `Protected` **onFieldSet**(`playerId`, `rankIndex`, `fieldId`, `fieldValue`, `textBlockIndex`, `textBlock`): `void` <Badge type="tip" text="client" />

设置字段内容后调用，需要请复写


#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `playerId` | `number` |  玩家id |
| `rankIndex` | `number` |  名次索引(0开始) |
| `fieldId` | `number` |  字段索引 (如果是排行字段，此参数为mull) |
| `fieldValue` | `string` \| `number` |  字段显示内容 |
| `textBlockIndex` | `number` |  文本控件索引 |
| `textBlock` | [`TextBlock`](UI.TextBlock.md) |  文本控件 |

