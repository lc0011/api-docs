[UTILITY](../groups/UTILITY.UTILITY.md) / LeaderboardModuleBaseC

# LeaderboardModuleBaseC<T\> <Badge type="tip" text="Class" /> <Score text="LeaderboardModuleBaseC<T\>" />

排行榜模块-客户端

## Type parameters

| Name | Type |
| :------ | :------ |
| `T` | extends [`LeaderboardModuleBaseS`](Extension.LeaderboardModuleBaseS.md)<`any`\> |

## Hierarchy

- [`ModuleC`](Extension.ModuleC.md)<`T`, ``null``\>

  ↳ **`LeaderboardModuleBaseC`**

## Table of contents

| Accessors |
| :-----|


::: details 点击查看继承
| Accessors |
| :-----|
| **[data](Extension.ModuleC.md#data)**(): `S` <br> currentPlayer的模块数据|
:::


| Methods |
| :-----|
| **[startRefreshPanel](Extension.LeaderboardModuleBaseC.md#startrefreshpanel)**(`refreshCallback`: (`playerDataList`: [`LeaderboardPlayerData`](../modules/Extension.Extension.md#leaderboardplayerdata)[]) => `void`, `timeInterval?`: `number`): `void` <br> 开始刷新界面|
| **[stopRefreshPanel](Extension.LeaderboardModuleBaseC.md#stoprefreshpanel)**(): `void` <br> 停止刷新界面|


::: details 点击查看继承
| Methods |
| :-----|
| **[onAwake](Extension.ModuleC.md#onawake)**(): `void` <br> 生命周期方法-创建模块时调用|
| **[onDestroy](Extension.ModuleC.md#ondestroy)**(): `void` <br> 生命周期方法-销毁模块调用|
| **[onEnterScene](Extension.ModuleC.md#onenterscene)**(`sceneType`: `number`): `void` <br> 生命周期方法-进入场景调用|
| **[onExecute](Extension.ModuleC.md#onexecute)**(`type`: `number`, `...params`: `any`[]): `void` <br> 外部调用本模块的某个操作|
| **[onStart](Extension.ModuleC.md#onstart)**(): `void` <br> 生命周期方法-启动模块时调用|
| **[onUpdate](Extension.ModuleC.md#onupdate)**(`dt`: `number`): `void` <br> 生命周期方法-刷新模块调用|
:::


## Methods
___

### startRefreshPanel <Score text="startRefreshPanel" /> 

• `Protected` **startRefreshPanel**(`refreshCallback`, `timeInterval?`): `void` <Badge type="tip" text="client" />

开始刷新界面


#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `refreshCallback` | (`playerDataList`: [`LeaderboardPlayerData`](../modules/Extension.Extension.md#leaderboardplayerdata)[]) => `void` |  刷新的回调方法，可以在这个方法里刷新UI |
| `timeInterval?` | `number` |  刷新的间隔时间(单位:秒)，这个时间越小，S端有变化时前端刷新越及时，但更消耗性能，建议使用默认值1秒 default: 1 |


___

### stopRefreshPanel <Score text="stopRefreshPanel" /> 

• `Protected` **stopRefreshPanel**(): `void` <Badge type="tip" text="client" />

停止刷新界面


