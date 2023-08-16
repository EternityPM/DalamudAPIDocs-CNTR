# 命名空间: Dalamud.Game.ClientState

## 类

### ClientState

该类表示访问游戏客户端时其的状态

**程序集：Dalamud.dll**

```c#
public sealed class ClientState : IDisposable, IServiceType, IClientState
```

#### 实现

- `System.IDisposable`
- [Dalamud.IServiceType](Dalamud.md#IServiceType)
- Dalamud.Plugin.Services.IClientState 【待补充链接】

#### 属性

##### ClientLanguage

获取客户端的语言

```c#
public ClientLanguage ClientLanguage { get; }
```

##### TerritoryType

获取玩家所在的区域

```c#
public ushort TerritoryType { get; }
```

##### LocalPlayer

如果存在，获取本地玩家角色

```c#
public PlayerCharacter? LocalPlayer { get; }
```

##### LocalContentId

获取本地角色的内容ID

```c#
public ulong LocalContentId { get; }
```

##### IsLoggedIn

获取一个值，该值指示是否已有一个角色登录

```c#
public bool IsLoggedIn { get; }
```

##### IsPvP

获取一个值，该值指示用户是否正在进行 PvP

```c#
public bool IsPvP { get; }
```

##### IsPvPExcludingDen

获取一个值，该值指示用户是否正在进行 PvP (不包含群狼盛宴)

```c#
public bool IsPvPExcludingDen { get; }
```

#### 事件

##### TerritoryChanged

当玩家当前所处区域更改时触发的事件

```c#
public event EventHandler<ushort> TerritoryChanged
```

###### 事件类型

`System.EventHandler<System.UInt16>`

##### Login

在角色登录时触发的事件，此时本地角色对象处于可用状态

```c#
public event EventHandler Login
```

###### 事件类型

`System.EventHandler`

##### Logout

在角色登出时触发的事件

```c#
public event EventHandler Logout
```

###### 事件类型

System.EventHandler`

##### EnterPvP

在角色进入 PvP 时触发的事件

```c#
public event Action EnterPvP
```

###### 事件类型

`System.Action`

##### LeavePvP

在角色离开 PvP 时触发的事件

```c#
public event Action LeavePvP
```

###### 事件类型

`System.Action`

##### CfPop

当玩家准备进入副本(广义:包括副本、特殊场景探索等等)时触发的事件

```c#
public event EventHandler<ContentFinderCondition> CfPop
```

###### 事件类型

###### `System.EventHandler<Lumina.Excel.GeneratedSheets.ContentFinderCondition>`

#### 实现

- `System.IDisposable`
- [Dalamud.IServiceType](Dalamud.md#IServiceType)
- Dalamud.Plugin.Services.IClientState 【待补充链接】

### ClientStateAddressResolver

客户端状态的内存地址解析器

**程序集: Dalamud.dll**

```c#
public sealed class ClientStateAddressResolver : BaseAddressResolver
```

**继承**

- `System.Object` -> `Dalamud.Game.BaseAddressResolver`

#### 属性

##### ObjectTable

获取角色表的地址(Gets the address of the actor table.) 【翻译待定】

```c#
public nint ObjectTable { get; }
```

##### BuddyList

获取伙伴(如: 专属陆行鸟、宠物、冒险者分队、亲信战友)列表的地址

```c#
public nint BuddyList { get; }
```

##### FateTablePtr

获取指向临危受命表的指针的地址

```c#
public nint FateTablePtr { get; }
```

##### GroupManager

获取队伍(小队、团队、战队)管理器的地址

```c#
public nint GroupManager { get; }
```

##### LocalContentId

获取本地内容 ID 的地址

```c#
public nint LocalContentId { get; }
```

##### JobGaugeData

获取职业量谱数据的地址

```c#
public nint JobGaugeData { get; }
```

##### KeyboardState

获取键盘状态的地址

```c#
public nint KeyboardState { get; }
```

##### KeyboardStateIndexArray

获取键盘状态索引数组的地址，该数组将 VK 枚举值转换为键盘状态

```c#
public nint KeyboardStateIndexArray { get; }
```

##### TargetManager

获取目标管理器的地址

```c#
public nint TargetManager { get; }
```

##### ConditionFlags

获取条件标志 (Flag) 数组的地址

```c#
public nint ConditionFlags { get; }
```

##### SetupTerritoryType

获取设置区域类型的方法的地址

```c#
public nint SetupTerritoryType { get; }
```

##### GamepadPoll

获取轮询游戏手柄数据的方法的地址。即使在设置中禁用了游戏手柄，也会以每帧一次的频率调用此方法

```c#
public nint GamepadPoll { get; }
```

#### 方法

##### Setup64Bit(SigScanner)

扫描并设置任何配置的地址指针

```c#
protected override void Setup64Bit(SigScanner sig)
```

###### 参数

| 类型                    | 名称 | 描述                        |
| ----------------------- | ---- | --------------------------- |
| `Dalamud.Game.SigScanner` | *sig* | 用于辅助设置的签名扫描器 |
