# 命名空间: Dalamud.Game

## 类

### BaseAddressResolver

基础内存地址解析器

**程序集：Dalamud.dll**

```c#
public abstract class BaseAddressResolver
```

**派生**：【待补充链接】

- Dalamud.Game.ClientState.ClientStateAddressResolver
- Dalamud.Game.DutyState.DutyStateAddressResolver
- [Dalamud.Game.FrameworkAddressResolver](#FrameworkAddressResolver)
- Dalamud.Game.Gui.ChatGuiAddressResolver
- Dalamud.Game.Gui.FlyText.FlyTextGuiAddressResolver
- Dalamud.Game.Gui.PartyFinder.PartyFinderAddressResolver
- Dalamud.Game.Gui.Toast.ToastGuiAddressResolver
- Dalamud.Game.Libc.LibcFunctionAddressResolver
- Dalamud.Game.Network.GameNetworkAddressResolver

#### 属性
##### DebugScannedValues
获取已发现的内存地址列表，以在 /xldata 中列出

```c#
public static Dictionary<string, List<(string ClassName, nint Address)>> DebugScannedValues { get; }
```

##### IsResolved
获取或设置一个值，指示解析器是否已成功运行 [Dalamud.Game.BaseAddressResolver.Setup32Bit(Dalamud.Game.SigScanner)](#Setup32Bit(SigScanner)) 或 [Dalamud.Game.BaseAddressResolver.Setup64Bit(Dalamud.Game.SigScanner)](#Setup64Bit(SigScanner))

```c#
protected bool IsResolved { get; set; }
```

#### 方法
##### Setup()
使用默认的 SigScanner 并根据进程架构调用适当的方法设置解析器

对于插件。不打算从 Dalamud Service{T} 构造函数中调用 (Not intended to be called from Dalamud Service{T} constructors) 【翻译待定】

```c#
[UsedImplicitly]
public void Setup()
```

##### Setup(SigScanner)
根据进程架构调用适当的方法设置解析器

```c#
public void Setup(SigScanner scanner)
```

###### 输入值
| 类型                  | 名称     | 描述               |
| --------------------- | -------- | ------------------ |
| Dalamud.Game.SigScanner | *scanner* | SigScanner 实例。 |

##### GetVirtualFunction<T>(nint, int, int)
从虚函数表指针获取第 N个虚函数，并返回一个委托函数指针

```c#
public T GetVirtualFunction<T>(nint address, int vtableOffset, int count) where T : class
```

###### 返回值
`<T>`：可调用的委托函数指针

###### 输入值
| 类型             | 名称       | 描述             |
| ---------------- | ---------- | ---------------- |
| `System.IntPtr`  | *address*  | 虚函数表的地址   |
| `System.Int32`   | *vtableOffset* | 从地址到虚函数表指针的偏移量 |
| `System.Int32`   | *count*    | 虚函数索引  |

###### 类型参数
| 名称 | 描述         |
| ---- | ------------ |
| `T`  | 用于将函数指针进行委托封装的委托 |

##### Setup32Bit(SigScanner)
通过查找任何必要的内存地址设置解析器

```c#
protected virtual void Setup32Bit(SigScanner scanner)
```

###### 输入值
| 类型                  | 名称     | 描述             |
| --------------------- | -------- | ---------------- |
| `Dalamud.Game.SigScanner` | *scanner* | SigScanner 实例 |

##### Setup64Bit(SigScanner)
通过查找任何必要的内存地址来设置解析器

```c#
protected virtual void Setup64Bit(SigScanner scanner)
```

###### 输入值
| 类型                  | 名称     | 描述             |
| --------------------- | -------- | ---------------- |
| `Dalamud.Game.SigScanner` | *scanner* | SigScanner 实例 |

##### SetupInternal(SigScanner)
通过查找任何必要的内存地址来设置解析器

```c#
protected virtual void SetupInternal(SigScanner scanner)
```

###### 输入值
| 类型                  | 名称     | 描述             |
| --------------------- | -------- | ---------------- |
| `Dalamud.Game.SigScanner` | *scanner* | SigScanner 实例。 |


### ChatHandlers

聊天相关的事件和公共辅助函数

**程序集: Dalamud.dll**

```c#
public class ChatHandlers : IServiceType
```

**实现:**

[Dalamud.IServiceType](Dalamud.md#IServiceType)

#### 属性

##### LastLink

获取聊天栏内最后出现的一条链接

```c#
public string? LastLink { get; }
```

##### IsAutoUpdateComplete

获取一个值，该值指示本次会话中是否已完成自动更新

```c#
public bool IsAutoUpdateComplete { get; }
```

#### 方法

##### MakeItalics(string)

将一个 TextPayload 转换为 SeString，并将其包装在斜体样式的有效载荷中中 (Convert a TextPayload to SeString and wrap in italics payloads) 【翻译待定】

```c#
public static SeString MakeItalics(string text)
```

###### 返回值

Dalamud.Game.Text.SeStringHandling.SeString 【链接待补充】: 带有斜体文本的 SeString 有效载荷

###### 输入值

| 类型            | 名称   | 描述         |
| --------------- | ------ | ------------ |
| `System.String` | *text* | 要转换的文本 |

##### MakeItalics(TextPayload)

将一个 TextPayload 转换为 SeString，并将其包装在斜体样式的有效载荷中中 (Convert a TextPayload to SeString and wrap in italics payloads) 【翻译待定】

```c#
public static SeString MakeItalics(TextPayload text)
```

###### 返回值

Dalamud.Game.Text.SeStringHandling.SeString 【链接待补充】: 带有斜体文本的 SeString 有效载荷

###### 输入值

| 类型            | 名称   | 描述         |
| --------------- | ------ | ------------ |
| `System.String` | *text* | 要转换的文本 |

#### 实现

- [Dalamud.IServiceType](Dalamud.md#IServiceType)

### Framwork

该类代表了原生游戏客户端的框架，并提供对各种子系统的访问

**程序集: Dalamud.dll**

```c#
public sealed class Framework : IDisposable, IServiceType
```

**实现:**

`System.IDisposable`, [Dalamud.IServiceType](Dalamud.md#IServiceType)

#### 属性

##### StatsEnabled

获取或设置一个值，该值指示是否启用统计数据收集

```c#
public static bool StatsEnabled { get; set; }
```

##### StatsHistory

获取统计数据历史映射

```c#
public static Dictionary<string, List<double>> StatsHistory { get; }
```

##### Address

获取 Client::Framework 实例的原始指针

```c#
public FrameworkAddressResolver Address { get; }
```

##### LastUpdate

获取上次触发 Framework Update 事件时的时间

```c#
public DateTime LastUpdate { get; }
```

##### LastUpdateUTC

获取上次触发 Framework Update 事件时的时间(以 UTC 表示)

```c#
public DateTime LastUpdateUTC { get; }
```

##### UpdateDelta

获取上次触发 Framework Update 事件时的事件与目前正在执行的 Framework Update 事件之间的时间间隔

```c#
public TimeSpan UpdateDelta { get; }
```

##### IsInFrameworkUpdateThread

获取一个值，该值指示当前执行的代码是否在游戏框架的更新线程中运行

```c#
public bool IsInFrameworkUpdateThread { get; }
```

##### IsFrameworkUnloading

获取一个值，该值指示游戏框架是否正在进行卸载操作

```c#
public bool IsFrameworkUnloading { get; }
```

#### 方法

##### RunOnFrameworkThread<T>(Func<T>)

如果从游戏的 Framwork.Update 线程调用了本函数，则立即运行给定的函数；否则，则在下一次 Framwork.Update 被调用时运行给定的函数

```c#
public Task<T> RunOnFrameworkThread<T>(Func<T> func)
```

###### 返回值

`System.Threading.Tasks.Task<<T>>`: 代表已经完成的或正在等待中的函数任务

###### 输入值

| 类型               | 名称   | 描述         |
| ------------------ | ------ | ------------ |
| `System.Func<<T>>` | *func* | 要调用的函数 |

###### 参数类型

| 名称 | 描述       |
| ---- | ---------- |
| `T`  | 返回的类型 |

##### RunOnFrameworkThread(Action)

如果从游戏的 Framwork.Update 线程调用了本函数，则立即运行给定的函数；否则，则在下一次 Framwork.Update 被调用时运行给定的函数

```c#
public Task RunOnFrameworkThread(Action action)
```

###### 返回值

`System.Threading.Tasks.Task<<T>>`: 代表已经完成的或正在等待中的函数任务

###### 输入值

| 类型            | 名称     | 描述         |
| --------------- | -------- | ------------ |
| `System.Action` | *action* | 要调用的函数 |

##### RunOnFrameworkThread<T>(Func<Task<T>>)

如果从游戏的 Framwork.Update 线程调用了本函数，则立即运行给定的函数；否则，则在下一次 Framwork.Update 被调用时运行给定的函数

```c#
public Task<T> RunOnFrameworkThread<T>(Func<Task<T>> func)
```

###### 返回值

`System.Threading.Tasks.Task<<T>>`: 代表已经完成的或正在等待中的函数任务

###### 输入值

| 类型                                            | 名称   | 描述         |
| ----------------------------------------------- | ------ | ------------ |
| `System.Func<System.Threading.Tasks.Task<<T>>>` | *func* | 要调用的函数 |

###### 参数类型

| 名称 | 描述       |
| ---- | ---------- |
| `T`  | 返回的类型 |

##### RunOnFrameworkThread(Func<Task>)

如果从游戏的 Framwork.Update 线程调用了本函数，则立即运行给定的函数；否则，则在下一次 Framwork.Update 被调用时运行给定的函数

```c#
public Task RunOnFrameworkThread(Func<Task> func)
```

###### 返回值

`System.Threading.Tasks.Task<<T>>`: 代表已经完成的或正在等待中的函数任务

###### 输入值

| 类型                                        | 名称   | 描述         |
| ------------------------------------------- | ------ | ------------ |
| `System.Func<System.Threading.Tasks.Tasks>` | *func* | 要调用的函数 |

##### RunOnTick<T>(Func<T>, TimeSpan, int, CancellationToken)

在接下来的 Framework.Tick 的调用中运行给定的函数

```c#
public Task<T> RunOnTick<T>(Func<T> func, TimeSpan delay = default, int delayTicks = 0, CancellationToken cancellationToken = default)
```

###### 返回值

`System.Threading.Tasks.Task<<T>>`: 代表正在等待中的函数任务

###### 输入值

| 类型                                 | 名称                | 描述                                                         |
| ------------------------------------ | ------------------- | ------------------------------------------------------------ |
| `System.Func<<T>>`                   | *func*              | 要调用的函数                                                 |
| `System.TimeSpan`                    | *delay*             | 调用给定函数前需要等待的时间间隔                             |
| `System.Int32`                       | *delayTicks*        | 调用给定函数前，计算给定数量的 Framewrok.Tick 调用次数。这一参数优先于延迟参数 |
| `System.Threading.CancellationToken` | *cancellationToken* | 当等待条件为满足时，用于阻止给定函数执行的取消令牌           |

###### 参数类型

| 名称 | 描述       |
| ---- | ---------- |
| `T`  | 返回的类型 |

##### RunOnTick(Action, TimeSpan, int, CancellationToken)

在接下来的 Framework.Tick 的调用中运行给定的函数

```c#
public Task RunOnTick(Action action, TimeSpan delay = default, int delayTicks = 0, CancellationToken cancellationToken = default)
```

###### 返回值

`System.Threading.Tasks.Task`: 代表正在等待中的函数任务

###### 输入值

| 类型                                 | 名称                | 描述                                                         |
| ------------------------------------ | ------------------- | ------------------------------------------------------------ |
| `System.Action`                      | *action*            | 要调用的函数                                                 |
| `System.TimeSpan`                    | *delay*             | 调用给定函数前需要等待的时间间隔                             |
| `System.Int32`                       | *delayTicks*        | 调用给定函数前，计算给定数量的 Framewrok.Tick 调用次数。这一参数优先于延迟参数 |
| `System.Threading.CancellationToken` | *cancellationToken* | 当等待条件为满足时，用于阻止给定函数执行的取消令牌           |

##### RunOnTick<T>(Func<Task<T>>, TimeSpan, int, CancellationToken)

在接下来的 Framework.Tick 的调用中运行给定的函数

```c#
public Task<T> RunOnTick<T>(Func<Task<T>> func, TimeSpan delay = default, int delayTicks = 0, CancellationToken cancellationToken = default)
```

###### 返回值

`System.Threading.Tasks.Task<<T>>`: 代表正在等待中的函数任务

###### 输入值

| 类型                                            | 名称                | 描述                                                         |
| ----------------------------------------------- | ------------------- | ------------------------------------------------------------ |
| `System.Func<System.Threading.Tasks.Task<<T>>>` | *func*              | 要调用的函数                                                 |
| `System.TimeSpan`                               | *delay*             | 调用给定函数前需要等待的时间间隔                             |
| `System.Int32`                                  | *delayTicks*        | 调用给定函数前，计算给定数量的 Framewrok.Tick 调用次数。这一参数优先于延迟参数 |
| `System.Threading.CancellationToken`            | *cancellationToken* | 当等待条件为满足时，用于阻止给定函数执行的取消令牌           |

###### 参数类型

| 名称 | 描述       |
| ---- | ---------- |
| `T`  | 返回的类型 |

##### RunOnTick(Func<Task>, TimeSpan, int, CancellationToken)

在接下来的 Framework.Tick 的调用中运行给定的函数

```c#
public Task RunOnTick(Func<Task> func, TimeSpan delay = default, int delayTicks = 0, CancellationToken cancellationToken = default)
```

###### 返回值

`System.Threading.Tasks.Task`: 代表正在等待中的函数任务

###### 输入值

| 类型                                 | 名称                | 描述                                                         |
| ------------------------------------ | ------------------- | ------------------------------------------------------------ |
| `System.Action`                      | *action*            | 要调用的函数                                                 |
| `System.TimeSpan`                    | *delay*             | 调用给定函数前需要等待的时间间隔                             |
| `System.Int32`                       | *delayTicks*        | 调用给定函数前，计算给定数量的 Framewrok.Tick 调用次数。这一参数优先于延迟参数 |
| `System.Threading.CancellationToken` | *cancellationToken* | 当等待条件为满足时，用于阻止给定函数执行的取消令牌           |

#### 事件

##### Update

每次游戏框架更新时触发的事件

```c#
public event Framework.OnUpdateDelegate Update
```

###### 事件类型

[Dalamud.Game.Framework.OnUpdateDelegate](#Framework.OnUpdateDelegate)

#### 实现

- `System.IDisposable`
- [Dalamud.IServiceType](Dalamud.md#IServiceType)

### FrameworkAddressResolver

为 [Dalamud.Game.Framwork](#Framwork) 类服务的地址解析器

**程序集: Dalamud.dll**

```c#
public sealed class FrameworkAddressResolver : BaseAddressResolver
```

**继承:** `System.Object` -> [Dalamud.Game.BaseAddressResolver](#BaseAddressResolver)

#### 属性

##### BaseAddress

获取 Framework 对象的基地址

```c#
[Obsolete("Please use FFXIVClientStructs.FFXIV.Client.System.Framework.Framework.Instance() instead.")]
public nint BaseAddress { get; }
```

##### DestroyAddress

获取在框架销毁时被调用一次的函数的地址

```c#
public nint DestroyAddress { get; }
```

##### FreeAddress

获取在框架释放时被调用一次的函数的地址

```c#
public nint FreeAddress { get; }
```

##### TickAddress

获取在每一 Tick 中被调用的函数

```c#
public nint TickAddress { get; }
```

#### 方法

##### Setup64Bit(SigScanner)

通过查找任何必要的内存地址设置解析器

```c#
protected override void Setup64Bit(SigScanner sig)
```

###### 传入值

| 类型                                   | 名称  |
| -------------------------------------- | ----- |
| [Dalamud.Game.SigScanner](#SigScanner) | `sig` |

### GameLifecycle

提供对常见游戏事件的取消标记

**程序集: Dalamud.dll**

```c#
public class GameLifecycle : IServiceType, IGameLifecycle
```

**实现:**

[Dalamud.IServiceType](Dalamud.md#IServiceType), Dalamud.Plugin.Services.IGameLifecycle 【待补充链接】

#### 属性

##### DalamudUnloadingToken

获取一个令牌，该令牌在 Dalamud 卸载时将被取消

```c#
public CancellationToken DalamudUnloadingToken { get; }
```

##### GameShuttingDownToken

获取一个令牌，该令牌在游戏关闭时将被取消

```c#
public CancellationToken GameShuttingDownToken { get; }
```

##### LogoutToken

获取一个令牌，该令牌在一个角色登出游戏时将被取消

```c#
public CancellationToken LogoutToken { get; }
```

#### 实现

- [Dalamud.IServiceType](Dalamud.md#IServiceType)
- Dalamud.Plugin.Services.IGameLifecycle

### GameVersion

一个 GameVersion 对象包含五个不同层次的数字部分: 年, 月, 日, 大版本号, 小版本号。这五个部分都可以不被指定，未被指定的部分内部则表示为 -1。根据定义，未指定的部分将会匹配任何值(包括已指定和未指定的值)，并且未指定的部分将“小于”任何指定的值。如果五个部分均未被指定，则其等同于字符串 “any”。这些值可以从你游戏安装目录的 ffxivgame.ver 文件中获取

**程序集: Dalamud.dll**

```c#
[Serializable]
public sealed class GameVersion : ICloneable, IComparable, IComparable<GameVersion>, IEquatable<GameVersion>
```

**实现:**
`System.ICloneable`, `System.IComparable`, `System.IComparable<Dalamud.Game.GameVersion>`, `System.IEquatable<Dalamud.Game.GameVersion>`

#### 属性

##### Any

获取默认的 "any" 游戏版本

```c#
public static GameVersion Any { get; }
```

##### Year

获取年份部分

```c#
public int Year { get; }
```

##### Month

获取月份部分

```c#
public int Month { get; }
```

##### Day

获取日数部分

```c#
public int Day { get; }
```

##### Major

获取游戏大版本号部分

```c#
public int Major { get; }
```

##### Minor

获取游戏小版本号部分

```c#
public int Minor { get; }
```

#### 方法

##### Parse(string)

解析一个代表版本的字符串，格式可以是"YYYY.MM.DD.majr.minr" 或 "any"

```c#
public static GameVersion Parse(string input)
```

###### 返回值

[Dalamud.Game.GameVersion](#GameVersion): GameVersion 对象

输入值

| 类型            | 名称    | 描述           |
| --------------- | ------- | -------------- |
| `System.String` | *input* | 待解析的字符串 |

##### TryParse(string, out GameVersion)

解析一个代表版本的字符串，格式可以是"YYYY.MM.DD.majr.minr" 或 "any"

```c#
public static bool TryParse(string input, out GameVersion result)
```

###### 返回值

`System.Boolean`: 解析成功或失败

输入值

| 类型                                     | 名称     | 描述             |
| ---------------------------------------- | -------- | ---------------- |
| `System.String`                          | *input*  | 待解析的字符串   |
| [Dalamud.Game.GameVersion](#GameVersion) | *result* | GameVersion 对象 |

##### Clone()

创建一个新对象，该对象为当前实例的副本

```c#
public object Clone()
```

###### 返回值

`System.Object`: 一个与当前实例相同的新对象的副本

##### CompareTo(object)

将当前实例与另一个相同类型的对象相比较，并返回一个整数，该整数指示当前实例在排序顺序中是位于比较对象之前还是相同的位置

```c#
public int CompareTo(object obj)
```

###### 返回值

`System.Int32`: 表示与比较对象的相对顺序，具有以下含义:

| 值   | 含义                                   |
| ---- | -------------------------------------- |
| < 0  | 在排序顺序中，当前实例位于比较对象之前 |
| = 0  | 在排序顺序中，当前实例与比较对象相同   |
| > 0  | 在排序顺序中，当前实例位于比较对象之后 |

###### 输入值

| 类型            | 名称  | 描述                 |
| --------------- | ----- | -------------------- |
| `System.Object` | *obj* | 与当前实例比较的对象 |

###### 异常

`System.ArgumentException`: 比较对象与当前实例非相同类型

### GameVersionConverter

将一个 Dalamud.Game.GameVersion 对象转换并组成一个字符串 (如: `2010.01.01.1234.5678`)

### SigScanner

用于在给定的进程模块 (ProcessModule) 中搜索内存签名

## 接口

### ISigScanner

用于在给定的进程模块 (ProcessModule) 中搜索内存签名

## 委托

### Framework.OnDestroyDelegate

用于原生 Framework::free 期间的委托

### Framework.OnRealDestroyDelegate

用于原生 Framework::destory 期间的委托

### Framework.OnUpdateDelegate

与 [Dalamud.Game.Framework.Update](#Update) 事件一起使用的委托

