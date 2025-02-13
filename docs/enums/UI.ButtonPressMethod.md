[GUI](../groups/GUI.GUI.md) / ButtonPressMethod

# ButtonPressMethod <Badge type="tip" text="Enumeration" /> <Score text="ButtonPressMethod" />

按钮按压响应规则

## Table of contents

| Enumeration Members |
| :-----|
| **[ButtonPress](UI.ButtonPressMethod.md#buttonpress)** = ``1`` <br> |
| **[ButtonRelease](UI.ButtonPressMethod.md#buttonrelease)** = ``2`` <br> |
| **[DownAndUp](UI.ButtonPressMethod.md#downandup)** = ``0`` <br> |

## Enumeration Members

### ButtonPress <Score text="ButtonPress" /> 

• **ButtonPress** = ``1``

按下按钮后，单击将立即触发。

___

### ButtonRelease <Score text="ButtonRelease" /> 

• **ButtonRelease** = ``2``

当焦点按钮上发生按钮释放时，始终会触发单击，
即使聚焦时没有按下按钮。

___

### DownAndUp <Score text="DownAndUp" /> 

• **DownAndUp** = ``0``

用户必须按下按钮，然后在按钮具有焦点时释放，以触发单击。
这是最常见的按钮类型。
