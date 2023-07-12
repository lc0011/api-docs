[GAMEPLAY](../groups/Core.GAMEPLAY.md) / Trigger

# Trigger <Badge type="tip" text="Class" /> <Score text="Trigger" />

触发器，对进入/离开触发器范围的事件进行响应

::: warning Precautions

各端运行，无自动同步

:::

使用示例:常用接口示例
```ts
// 将如下脚本挂载至对象管理器触发器下
@Class
export default class TriggerExample extends Script {
    //当脚本被实例后，会在第一帧更新前调用此函数
    protected async onStart(): Promise<void> {
        // 获取当前脚本所挂载的触发器
        let Trigger = this.gameObject as Trigger
        // 对进入触发器事件进行绑定
        Trigger.onEnter.add((obj) => {
            // 输出Log
            console.log("OnEnter:" + obj.name);
        });
        // 对离开触发器事件进行绑定
        Trigger.onLeave.add((obj) => {
            // 输出Log
            console.log("OnLeave:" + obj.name);
        });
    }
}
```

## Hierarchy

- [`GameObject`](mw.GameObject.md)

  ↳ **`Trigger`**

## Table of contents

| Properties |
| :-----|
| **[onEnter](mw.Trigger.md#onenter)**: [`MulticastDelegate`](mw.MulticastDelegate.md)<(`gameObject`: [`GameObject`](mw.GameObject.md)) => `void`\> <br> 进入触发器事件|
| **[onLeave](mw.Trigger.md#onleave)**: [`MulticastDelegate`](mw.MulticastDelegate.md)<(`gameObject`: [`GameObject`](mw.GameObject.md)) => `void`\> <br> 离开触发器事件|


::: details 点击查看继承
| Properties |
| :-----|
| **[onDestroyDelegate](mw.GameObject.md#ondestroydelegate)**: [`MulticastDelegate`](mw.MulticastDelegate.md)<() => `void`\> <br> 物体Destroy事件回调|
:::


| Accessors |
| :-----|
| **[enabled](mw.Trigger.md#enabled)**(): `boolean` <br> 是否已启用|
| **[shape](mw.Trigger.md#shape)**(): [`TriggerShapeType`](../enums/mw.TriggerShapeType.md) <br> 触发器形状|
| **[shapeExtent](mw.Trigger.md#shapeextent)**(): [`Vector`](mw.Vector.md) <br> 触发器形状，当形状为 Box 时，大小为 Vector；当形状为 Sphere 时，大小取返回值的 Z 轴的值|


::: details 点击查看继承
| Accessors |
| :-----|
| **[guid](mw.GameObject.md#guid)**(): `string` <br> 获取对象的GUID（唯一标识一个对象的字符串）。|
| **[isLocked](mw.GameObject.md#islocked)**(): `boolean` <br> 获取对象是否锁定|
| **[isReady](mw.GameObject.md#isready)**(): `boolean` <br> 当前物体状态|
| **[isStatic](mw.GameObject.md#isstatic)**(): `boolean` <br> 获取对象是否静态|
| **[localTransform](mw.GameObject.md#localtransform)**(): [`Transform`](mw.Transform.md) <br> 当前物体本地transform|
| **[name](mw.GameObject.md#name)**(): `string` <br> 返回当前物体名称|
| **[netStatus](mw.GameObject.md#netstatus)**(): [`NetStatus`](../enums/mw.NetStatus.md) <br> 获取当前物体同步状态|
| **[parent](mw.GameObject.md#parent)**(): [`GameObject`](mw.GameObject.md) <br> 获取当前父物体|
| **[sourceAssetGuid](mw.GameObject.md#sourceassetguid)**(): `string` <br> 获取当前物体使用资源的GUID|
| **[tag](mw.GameObject.md#tag)**(): `string` <br> 获取当前物体的Tag|
| **[useUpdate](mw.GameObject.md#useupdate)**(): `boolean` <br> 获取对象是否使用更新|
| **[worldTransform](mw.GameObject.md#worldtransform)**(): [`Transform`](mw.Transform.md) <br> 当前物体世界transform|
:::


| Methods |
| :-----|
| **[checkInArea](mw.Trigger.md#checkinarea)**(`gameObject`: [`GameObject`](mw.GameObject.md)): `boolean` <br> 判断指定对象是否在触发器区域|
| **[setBoxExtent](mw.Trigger.md#setboxextent)**(`InBoxExtent`: [`Vector`](mw.Vector.md), `updateOverlaps?`: `boolean`): `void` <br> 设置立方体触发器大小|
| **[setSphereRadius](mw.Trigger.md#setsphereradius)**(`InSphereRadius`: `number`, `updateOverlaps?`: `boolean`): `void` <br> 设置球形触发器大小|


::: details 点击查看继承
| Methods |
| :-----|
| **[asyncReady](mw.GameObject.md#asyncready)**(): `Promise`<[`GameObject`](mw.GameObject.md)\> <br> GameObject准备好后返回|
| **[attachToGameObject](mw.GameObject.md#attachtogameobject)**(`obj`: [`GameObject`](mw.GameObject.md)): `void` <br> 将物体附着到指定物体上|
| **[clone](mw.GameObject.md#clone)**(`spawnInfo?`: `boolean` \): [`GameObject`](mw.GameObject.md) <br> 复制对象|
| **[destroy](mw.GameObject.md#destroy)**(): `void` <br> 删除对象|
| **[detachFromGameObject](mw.GameObject.md#detachfromgameobject)**(): `void` <br> 将此物体与当前附着的物体分离|
| **[getBoundingBoxSize](mw.GameObject.md#getboundingboxsize)**(`nonColliding?`: `boolean`, `includeFromChildActors?`: `boolean`, `outer?`: [`Vector`](mw.Vector.md)): [`Vector`](mw.Vector.md) <br> 获取物体包围盒大小|
| **[getBounds](mw.GameObject.md#getbounds)**(`onlyCollidingComponents`: `boolean`, `OriginOuter`: [`Vector`](mw.Vector.md), `BoxExtentOuter`: [`Vector`](mw.Vector.md), `includeFromChildActors?`: `boolean`): `void` <br> 获取GameObject边界|
| **[getChildByGuid](mw.GameObject.md#getchildbyguid)**(`GUID`: `string`): `undefined` \| [`GameObject`](mw.GameObject.md) <br> 根据GUID查找子物体|
| **[getChildByName](mw.GameObject.md#getchildbyname)**(`name`: `string`): `undefined` \| [`GameObject`](mw.GameObject.md) <br> 根据名称查找子物体|
| **[getChildByPath](mw.GameObject.md#getchildbypath)**(`path`: `string`): [`GameObject`](mw.GameObject.md) <br> 根据路径查找子物体|
| **[getChildren](mw.GameObject.md#getchildren)**(): `undefined` \| [`GameObject`](mw.GameObject.md)[] <br> 获取Children|
| **[getChildrenBoxCenter](mw.GameObject.md#getchildrenboxcenter)**(`outer?`: [`Vector`](mw.Vector.md)): [`Vector`](mw.Vector.md) <br> 获取所有子对象包围盒中心点(不包含父对象,父对象不可用返回[0,0,0])|
| **[getChildrenByName](mw.GameObject.md#getchildrenbyname)**(`name`: `string`): [`GameObject`](mw.GameObject.md)[] <br> 通过名字查找所有的子物体|
| **[getScriptByGuid](mw.GameObject.md#getscriptbyguid)**(`GUID`: `string`): `undefined` \| `Script` <br> 获得当前物体下的指定脚本|
| **[getScriptByName](mw.GameObject.md#getscriptbyname)**(`name`: `string`): `undefined` \| `Script` <br> 获得当前物体下的指定脚本|
| **[getScripts](mw.GameObject.md#getscripts)**(): `undefined` \| `Script`[] <br> 获得当前物体下的所有脚本|
| **[getVisibility](mw.GameObject.md#getvisibility)**(): `boolean` <br> 获取GameObject是否被显示|
| **[isRunningClient](mw.GameObject.md#isrunningclient)**(): `boolean` <br> 是否为客户端|
| **[onDestroy](mw.GameObject.md#ondestroy)**(): `void` <br> 周期函数 被销毁时调用|
| **[onReplicated](mw.GameObject.md#onreplicated)**(`path`: `string`, `value`: `unknown`, `oldVal`: `unknown`): `void` <br> 属性被同步事件 ClientOnly|
| **[onStart](mw.GameObject.md#onstart)**(): `void` <br> 周期函数 脚本开始执行时调用|
| **[onUpdate](mw.GameObject.md#onupdate)**(`dt`: `number`): `void` <br> 周期函数 useUpdate 设置为 true 后,每帧被执行,设置为false,不会执行|
| **[setVisibility](mw.GameObject.md#setvisibility)**(`status`: [`PropertyStatus`](../enums/mw.PropertyStatus.md), `propagateToChildren?`: `boolean`): `void` <br> 设置GameObject是否被显示|
| **[asyncFindGameObjectByGuid](mw.GameObject.md#asyncfindgameobjectbyguid)**(`guid`: `string`): `Promise`<[`GameObject`](mw.GameObject.md)\> <br> 通过guid异步查找GameObject,默认是10秒,可以通过 `ScriptingSettings..setGlobalAsyncOverTime(1000 * 10);|
| **[asyncGetGameObjectByPath](mw.GameObject.md#asyncgetgameobjectbypath)**(`path`: `string`): `Promise`<[`GameObject`](mw.GameObject.md)\> <br> 通过路径异步查找物体|
| **[asyncSpawn](mw.GameObject.md#asyncspawn)**<`T`: extends [`GameObject`](mw.GameObject.md)<`T`\>\>(`spawnInfo`: [`GameObjectInfo`](../interfaces/mw.GameObjectInfo.md)): `Promise`<`T`: extends [`GameObject`](mw.GameObject.md)<`T`\>\> <br> 异步构造一个 GameObject 资源不存在会先去下载资源再去创建|
| **[findGameObjectByGuid](mw.GameObject.md#findgameobjectbyguid)**(`guid`: `string`): [`GameObject`](mw.GameObject.md) <br> 通过guid查找GameObject|
| **[findGameObjectByName](mw.GameObject.md#findgameobjectbyname)**(`name`: `string`): `undefined` \| [`GameObject`](mw.GameObject.md) <br> 通过名字查找物体|
| **[findGameObjectsByName](mw.GameObject.md#findgameobjectsbyname)**(`name`: `string`): [`GameObject`](mw.GameObject.md)[] <br> 通过名字查找物体|
| **[findGameObjectsByTag](mw.GameObject.md#findgameobjectsbytag)**(`tag`: `string`): [`GameObject`](mw.GameObject.md)[] <br> 通过自定义tag获取GameObject|
| **[getGameObjectByPath](mw.GameObject.md#getgameobjectbypath)**(`path`: `string`): [`GameObject`](mw.GameObject.md) <br> 通过路径查找物体|
| **[spawn](mw.GameObject.md#spawn)**<`T`: extends [`GameObject`](mw.GameObject.md)<`T`\>\>(`guid`: `string`, `position?`: [`Vector`](mw.Vector.md)): `T`: extends [`GameObject`](mw.GameObject.md)<`T`\> <br> 构造一个 GameObject|
:::


### onEnter <Score text="onEnter" /> 

• **onEnter**: [`MulticastDelegate`](mw.MulticastDelegate.md)<(`gameObject`: [`GameObject`](mw.GameObject.md)) => `void`\>

进入触发器事件

___

### onLeave <Score text="onLeave" /> 

• **onLeave**: [`MulticastDelegate`](mw.MulticastDelegate.md)<(`gameObject`: [`GameObject`](mw.GameObject.md)) => `void`\>

离开触发器事件

## Accessors

### enabled <Score text="enabled" /> 

• `get` **enabled**(): `boolean`

是否已启用

#### Returns

`boolean`

• `set` **enabled**(`value`): `void`

是否已启用

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `boolean` |


___

### shape <Score text="shape" /> 

• `get` **shape**(): [`TriggerShapeType`](../enums/mw.TriggerShapeType.md)

触发器形状

#### Returns

[`TriggerShapeType`](../enums/mw.TriggerShapeType.md)

• `set` **shape**(`value`): `void`

触发器形状

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | [`TriggerShapeType`](../enums/mw.TriggerShapeType.md) |


___

### shapeExtent <Score text="shapeExtent" /> 

• `get` **shapeExtent**(): [`Vector`](mw.Vector.md)

触发器形状，当形状为 Box 时，大小为 Vector；当形状为 Sphere 时，大小取返回值的 Z 轴的值

#### Returns

[`Vector`](mw.Vector.md)

• `set` **shapeExtent**(`value`): `void`

触发器形状，当形状为 Box 时，大小为 Vector；当形状为 Sphere 时，大小取参数的 Z 轴的值

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | [`Vector`](mw.Vector.md) |



## Methods
___

### checkInArea <Score text="checkInArea" /> 

• **checkInArea**(`gameObject`): `boolean` 

判断指定对象是否在触发器区域


#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `gameObject` | [`GameObject`](mw.GameObject.md) | 传入需判断的对象 |

#### Returns

`boolean`

true:为在触发器范围内

___

### setBoxExtent <Score text="setBoxExtent" /> 

• **setBoxExtent**(`InBoxExtent`, `updateOverlaps?`): `void` 

设置立方体触发器大小


#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `InBoxExtent` | [`Vector`](mw.Vector.md) | 盒体长宽高 |
| `updateOverlaps?` | `boolean` | 是否刷新 default:true |


___

### setSphereRadius <Score text="setSphereRadius" /> 

• **setSphereRadius**(`InSphereRadius`, `updateOverlaps?`): `void` 

设置球形触发器大小


#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `InSphereRadius` | `number` | 球体半径 |
| `updateOverlaps?` | `boolean` | 是否刷新 default:true |
