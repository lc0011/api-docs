[EXTENSION](../groups/Extension.EXTENSION.md) / ModuleManager

# ModuleManager <Badge type="tip" text="Class" /> <Score text="ModuleManager" />

模块管理

使用示例:创建一个名为ModuleExample的脚本，放置在对象栏中，打开脚本，将原本内容修改为如下内容，保存并运行游戏，客户端日志会先输出hud模块开始的日志，再输出player模块开始的日志，按下F键和G键你在客户端日志都会看到player模块的信息
```ts
@Class
export default class ModuleExample extends Script {

    protected onStart(): void {
        ModuleManager.setClientFirstStartModule(HudModuleC);
        ModuleManager.registerModule(PlayerModuleS, PlayerModuleC, PlayerModuleData);
        ModuleManager.registerModule(HudModuleS, HudModuleC, HudModuleData);
    }

}

class HudModuleC extends ModuleC<HudModuleS, HudModuleData>{
    protected onStart(): void {
        console.log("-----------客户端-hud模块开始-----------");
    }
    protected onExecute(type: number, ...params: any[]): void {
        switch (type) {
            case 0:
                //优先启动模块需要在onExecute中type为0调用该函数,编辑器会等待fun执行完毕后再执行其他模块的onStart
                this.onExecuteStart(params[0]);
                break;
            case 1:
                this.traceHudExecute(params[0], params[1], params[2]);
                break;
        }
    }
    //优先启动模块需要在onExecute中调用该函数,编辑器会等待fun执行完毕后再执行其他模块的onStart
    protected async onExecuteStart(fun: Function): Promise<void> {
        await TimeUtil.delaySecond(1);
        console.log("-----------客户端-hud模块准备结束-----------");
        fun();
    }

    //通过callExecute调用
    private traceHudExecute(testNum: number, testPos: mw.Vector, testString: string): void {
        console.log("-----------客户端-hud模块被调用-----------");
        console.log("testNum:" + testNum);
        console.log("testPos:" + testPos.x, testPos.y, testPos.z);
        console.log("testString:" + testString);
    }

    //直接调用
    public traceHud(testNum: number, testPos: mw.Vector, testString: string): void {
        console.log("-----------客户端-hud模块被调用-----------");
        console.log("testNum:" + testNum);
        console.log("testPos:" + testPos.x, testPos.y, testPos.z);
        console.log("testString:" + testString);
    }

}

class HudModuleS extends ModuleS<HudModuleC, HudModuleData>{

}

class HudModuleData extends Subdata {

}

class PlayerModuleC extends ModuleC<PlayerModuleS, PlayerModuleData>{
    protected onStart(): void {
        console.log("-----------客户端-player模块开始-----------");
        InputUtil.onKeyDown(Keys.F, () => {
            let playerData = this.data;
            ModuleManager.callExecute(HudModuleC, 1, playerData.getLevel(), playerData.getPos(), playerData.getName());
        })
        InputUtil.onKeyDown(Keys.G, () => {
            let playerData = this.data;
            let hudModuleC = ModuleManager.getModule(HudModuleC);
            hudModuleC.traceHud(playerData.getLevel(), playerData.getPos(), playerData.getName());
        })
    }
}
class PlayerModuleS extends ModuleS<PlayerModuleC, PlayerModuleData>{

}
class PlayerModuleData extends Subdata {
    @Decorator.saveProperty
    private level: number = 1;
    @Decorator.saveProperty
    private pos: mw.Vector = new mw.Vector(0, 0, 0);
    @Decorator.saveProperty
    private name: string = "test";

    public getLevel(): number {
        return this.level;
    }

    public getPos(): mw.Vector {
        return this.pos;
    }

    public getName(): string {
        return this.name;
    }
}
```

## Table of contents

| Methods |
| :-----|
| **[callExecute](mwext.ModuleManager.md#callexecute)**<`T`: extends [`ModuleS`](mwext.ModuleS.md)<`any`, `any`\> \\>(`moduleClass`: [`TypeName`](../interfaces/mw.TypeName.md)<`T`\>, `type?`: `number`, `...params`: `any`[]): `any` <br> 调用一个模块的onExecute方法|
| **[getModule](mwext.ModuleManager.md#getmodule)**<`T`: extends [`ModuleS`](mwext.ModuleS.md)<`any`, `any`\> \\>(`ModuleClass`: [`TypeName`](../interfaces/mw.TypeName.md)<`T`\>): `T`: extends [`ModuleS`](mwext.ModuleS.md)<`any`, `any`\> \ <br> 根据类型获取一个模块|
| **[getUpdateTimeLog](mwext.ModuleManager.md#getupdatetimelog)**(): `string` <br> 获取各模块update方法的执行时长，以字符串的形式返回，需要自己显示或打印出来|
| **[ready](mwext.ModuleManager.md#ready)**(): `Promise`<`void`\> <br> 判断ModuleManager是否就绪的异步方法|
| **[registerModule](mwext.ModuleManager.md#registermodule)**(`ServerModuleType`: [`TypeName`](../interfaces/mw.TypeName.md)<[`ModuleS`](mwext.ModuleS.md)<`any`, `any`\>\>, `ClientModuleType`: [`TypeName`](../interfaces/mw.TypeName.md)<[`ModuleC`](mwext.ModuleC.md)<`any`, `any`\>\>, `ModuleDataType?`: [`TypeName`](../interfaces/mw.TypeName.md)<[`Subdata`](mwext.Subdata.md)\>): [`ModuleManager`](mwext.ModuleManager.md) <br> 注册模块|
| **[setClientFirstStartModule](mwext.ModuleManager.md#setclientfirststartmodule)**(`ModuleClass`: [`TypeName`](../interfaces/mw.TypeName.md)<[`ModuleC`](mwext.ModuleC.md)<`any`, `any`\>\>): [`ModuleManager`](mwext.ModuleManager.md) <br> 设置客户端第一个要启动的模块|

## Methods

### callExecute <Score text="callExecute" /> 

• `Static` **callExecute**<`T`\>(`moduleClass`, `type?`, `...params`): `any` 

调用一个模块的onExecute方法


#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | extends [`ModuleS`](mwext.ModuleS.md)<`any`, `any`\> \| [`ModuleC`](mwext.ModuleC.md)<`any`, `any`\> |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `moduleClass` | [`TypeName`](../interfaces/mw.TypeName.md)<`T`\> |  模块 |
| `type?` | `number` |  给onExecute方法传递的操作类型，需要各个模块自己定义 default: 0 |
| `...params` | `any`[] |  给onExecute方法传递的参数，需要各个模块自己定义 |

#### Returns

`any`

onExecute方法return的结果

___

### getModule <Score text="getModule" /> 

• `Static` **getModule**<`T`\>(`ModuleClass`): `T` 

根据类型获取一个模块


#### Type parameters

| Name | Type |
| :------ | :------ |
| `T` | extends [`ModuleS`](mwext.ModuleS.md)<`any`, `any`\> \| [`ModuleC`](mwext.ModuleC.md)<`any`, `any`\> |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `ModuleClass` | [`TypeName`](../interfaces/mw.TypeName.md)<`T`\> |  模块类型 |

#### Returns

`T`

模块对象

___

### getUpdateTimeLog <Score text="getUpdateTimeLog" /> 

• `Static` **getUpdateTimeLog**(): `string` 

获取各模块update方法的执行时长，以字符串的形式返回，需要自己显示或打印出来


::: warning Precautions

本方法只有开启ModuleManager的debug才会生效，此方法有性能消耗，只用作性能分析，正式版本不要使用

:::

#### Returns

`string`

log字符串

___

### ready <Score text="ready" /> 

• `Static` **ready**(): `Promise`<`void`\> 

判断ModuleManager是否就绪的异步方法


#### Returns

`Promise`<`void`\>

异步操作的Promise

___

### registerModule <Score text="registerModule" /> 

• `Static` **registerModule**(`ServerModuleType`, `ClientModuleType`, `ModuleDataType?`): [`ModuleManager`](mwext.ModuleManager.md) 

注册模块


#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `ServerModuleType` | [`TypeName`](../interfaces/mw.TypeName.md)<[`ModuleS`](mwext.ModuleS.md)<`any`, `any`\>\> |  模块的服务端类型 |
| `ClientModuleType` | [`TypeName`](../interfaces/mw.TypeName.md)<[`ModuleC`](mwext.ModuleC.md)<`any`, `any`\>\> |  模块的客户端类型 |
| `ModuleDataType?` | [`TypeName`](../interfaces/mw.TypeName.md)<[`Subdata`](mwext.Subdata.md)\> |  模块的数据类型 default: null |

#### Returns

[`ModuleManager`](mwext.ModuleManager.md)

ModuleManager自身，可用作链式调用

___

### setClientFirstStartModule <Score text="setClientFirstStartModule" /> 

• `Static` **setClientFirstStartModule**(`ModuleClass`): [`ModuleManager`](mwext.ModuleManager.md) <Badge type="tip" text="client" />

设置客户端第一个要启动的模块


#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `ModuleClass` | [`TypeName`](../interfaces/mw.TypeName.md)<[`ModuleC`](mwext.ModuleC.md)<`any`, `any`\>\> |  模块类 |

#### Returns

[`ModuleManager`](mwext.ModuleManager.md)

ModuleManager自身，可用作链式调用