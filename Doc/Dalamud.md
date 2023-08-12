# 命名空间 : Dalamud

## 类

### ClientLanguageExtensions

为 [Dalamud.ClientLanguage](#ClientLanguage) 类提供的扩展方法

**程序集: Dalamud.dll**

```c#
public static class ClientLanguageExtensions
```

#### 方法

##### ToLumina(ClientLanguage)

将一个 Dalamud ClientLanguage 转为相应的 Lumina 变体

```c#
public static Language ToLumina(this ClientLanguage language)
```

###### 返回值

`Lumina.Data.Language`: 转换后的语言

###### 输入值

| 类型                                      | 名称       | 描述         |
| ----------------------------------------- | ---------- | ------------ |
| [Dalamud.ClientLanguage](#ClientLanguage) | *language* | 要转换的语言 |

### DalamudStartInfo

保存着初始化 Dalamud 所需信息的结构体

**程序集: Dalamud.dll**

```c#
[Serializable]
public record DalamudStartInfo : IServiceType, IEquatable<DalamudStartInfo>
```

**实现:**

[Dalamud.IServiceType](#IServiceType),`System.IEquatable<Dalamud.DalamudStartInfo>` 

#### 属性

##### WorkingDirectory

获取或设置 XIVLauncher 安装的工作目录

```c#
public string? WorkingDirectory { get; set; }
```

##### ConfigurationPath

获取或设置配置文件的路径

```c#
public string? ConfigurationPath { get; set; }
```

##### LogPath

获取或设置日志文件的路径

```c#
public string? LogPath { get; set; }
```

##### LogName

获取或设置日志文件的名称

```c#
public string? LogName { get; set; }
```

##### PluginDirectory

获取或设置安装插件的目录的路径

```c#
public string? PluginDirectory { get; set; }
```

##### AssetDirectory

获取或设置 Dalamud 核心资源文件的路径

```c#
public string? AssetDirectory { get; set; }
```

##### Language

获取或设置游戏客户端的语言

```c#
public ClientLanguage Language { get; set; }
```

##### GameVersion

获取或设置当前游戏的版本号

```c#
[JsonConverter(typeof(GameVersionConverter))]
public GameVersion? GameVersion { get; set; }
```

##### TroubleshootingPackData

获取或设置在生成 tspack 文件时要附加的故障排除信息

```c#
public string TroubleshootingPackData { get; set; }
```

##### DelayInitializeMs

获取或设置一个值，该值指定开始一个新的 Dalamud 会话前所要等待的具体时间

```c#
public int DelayInitializeMs { get; set; }
```

##### NoLoadPlugins

获取或设置一个值，该值指定是否应该不加载任何插件

```c#
public bool NoLoadPlugins { get; set; }
```

##### NoLoadThirdPartyPlugins

获取或设置一个值，该值指定是否应该不加载任何第三方插件

```c#
public bool NoLoadThirdPartyPlugins { get; set; }
```

##### BootLogPath

获取或设置引导启动文件被写入的路径

```c#
public string? BootLogPath { get; set; }
```

##### BootShowConsole

获取或设置一个值，该值指定是否显示一个启动控制台

```c#
public bool BootShowConsole { get; set; }
```

##### BootDisableFallbackConsole

获取或设置一个值，该值指定是否在必要情况下显示一个回退控制台

```c#
public bool BootDisableFallbackConsole { get; set; }
```

##### BootWaitMessageBox

获取或设置一个标志位，该标志位指定 Dalamud 应在何处等待一个消息框的出现

```c#
public int BootWaitMessageBox { get; set; }
```

##### BootWaitDebugger

获取或设置一个值，该值指定是否 Dalamud 应该等待被调试器注入后再初始化

```c#
public bool BootWaitDebugger { get; set; }
```

##### BootVehEnabled

获取或设置一个值，该值指定是否启用 VEH

```c#
public bool BootVehEnabled { get; set; }
```

##### BootVehFull

获取或设置一个值，该值指定 VEH 是否进行完整的崩溃转储

```c#
public bool BootVehFull { get; set; }
```

##### BootEnableEtw

获取或设置一个值，该值指定是否启用 ETW

```c#
public bool BootEnableEtw { get; set; }
```

##### BootDotnetOpenProcessHookMode

获取或设置一个选择 OpenProcess 钩子模式(hookmode)的值

```c#
public int BootDotnetOpenProcessHookMode { get; set; }
```

##### BootEnabledGameFixes

获取或设置一个已启用的游戏修复的列表

```c#
public List<string>? BootEnabledGameFixes { get; set; }
```

##### BootUnhookDlls

获取或设置一个应该被解除钩子的DLL的列表

```c#
public List<string>? BootUnhookDlls { get; set; }
```

##### CrashHandlerShow

获取或设置一个值，该值指定是否显示崩溃处理控制台窗口

```c#
public bool CrashHandlerShow { get; set; }
```

#### 实现

- [Dalamud.IServiceType](#IServiceType)
- `System.IEquatable<Dalamud.DalamudStartInfo>`

### EntryPoint

Dalamud 系统的主要入口点

**程序集: Dalamud.dll**

#### 字段

##### LogLevelSwitch

用于更改运行时日志级别的运行时日志级别切换

```c#
public static readonly LoggingLevelSwitch LogLevelSwitch
```

#### 方法

##### Initialize(nint, nint)

初始化 Dalamud

```c#
public static void Initialize(nint infoPtr, nint mainThreadContinueEvent)
```

###### 输入值

| 类型            | 名称                      | 描述                                                         |
| --------------- | ------------------------- | ------------------------------------------------------------ |
| `System.IntPtr` | *infoPtr*                 | 指向序列化的 [Dalamud.DalamudStartInfo](#DalamudStartInfo) 数据的指针 |
| `System.IntPtr` | *mainThreadContinueEvent* | 用于通知主线程继续的事件                                     |

##### VehCallback()

返回堆栈跟踪

```c#
public static nint VehCallback()
```

###### 返回值

`System.IntPtr`: HGlobal 转换为 wchar_t* 堆栈跟踪 C 字符串。

### Localization

处理本地化的类

**程序集: Dalamud.dll**

```c#
public class Localization : IServiceType
```

**实现**

[Dalamud.IServiceType](#IServiceType)

#### 字段

##### ApplicableLangCodes

在 Dalamud 中具有有效翻译的语言代码数组

```c#
public static readonly string[] ApplicableLangCodes
```

#### 方法

##### Localize(string, string)

在预设程序集中根据给定的字符串键搜索设置好的本地化数据，并返回它。如果键不存在，则显示备用文本，备用文本也是必须的，其用于创建需要本地化的字符串文件

```c#
public static string Localize(string key, string fallBack)
```

###### 返回值

`System.String`: 存储本地化文本或者备用文本的字符串，如果什么都没找到，则返回字符串键

###### 输入值

| 类型            | 名称       | 描述                         |
| --------------- | ---------- | ---------------------------- |
| `System.String` | *key*      | 用于被返回的字符串键         |
| `System.String` | *fallBack* | 备用字符串，一般为你的源语言 |

##### SetupWithUiCulture()

将界面语言按照用户的本地语言和文化偏好进行设置

```c#
public void SetupWithUiCulture()
```

##### SetupWithFallbacks()

将界面语言设置为备用语言文本(原本的英文文本)

```c#
public void SetupWithFallbacks()
```

##### SetupWithLangCode(string)

将界面语言设置为输入的语言代码代表的语言

```c#
public void SetupWithLangCode(string langCode)
```

###### 输入值

| 类型            | 名称       | 描述                       |
| --------------- | ---------- | -------------------------- |
| `System.String` | *langCode* | 用于设置界面语言的语言代码 |

##### ExportLocalizable(bool)

保存预设程序集的本地化 JSON 数据文件至当前工作目录

```c#
public void ExportLocalizable(bool ignoreInvalidFunctions = false)
```

###### 输入值

| 类型             | 名称                     | 描述                                                       |
| ---------------- | ------------------------ | ---------------------------------------------------------- |
| `System.Boolean` | *ignoreInvalidFunctions* | 假如设置为true，则忽略错误的 Localize 函数，而不是抛出错误 |

#### 事件

##### LocalizationChanged

当语言改变时触发的事件

```c#
public event Localization.LocalizationChangedDelegate LocalizationChanged
```

###### 事件类型

Dalamud.Localization.LocalizationChangedDelegate

#### 实现

- [Dalamud.IServiceType](#IServiceType)

### SafeMemory

用于实现安全内存访问的类

## 接口

### IServiceType

用于服务(Service)类型的标记类

**程序集: Dalamud.dll**

```c#
public static class SafeMemory
```

#### 方法

##### ReadBytes(nint, int, out byte[])

从当前进程读取一个字节数组

```c#
public static bool ReadBytes(nint address, int count, out byte[] buffer)
```

###### 返回值

`System.Boolean`: 读取是否成功

###### 输入值

| 类型            | 名称      | 描述               |
| --------------- | --------- | ------------------ |
| `System.IntPtr` | *address* | 要读取的进程的地址 |
| `System.Int32`  | *count*   | 要读取的字节数     |
| `System.Byte[]` | *buffer*  | 结果缓冲区         |

##### WriteBytes(nint, byte[])

为当前进程写入一个字节数组

```c#
public static bool WriteBytes(nint address, byte[] buffer)
```

###### 返回值

`System.Boolean`: 写入是否成功

###### 输入值

| 类型            | 名称      | 描述               |
| --------------- | --------- | ------------------ |
| `System.IntPtr` | *address* | 要写入的进程的地址 |
| `System.Byte[]` | *buffer*  | 写入缓冲区         |

##### Read<T>(nint, out T)

从当前进程读取指定结构体的对象

```c#
public static bool Read<T>(nint address, out T result) where T : struct
```

###### 返回值

`System.Boolean`: 读取是否成功

###### 输入值

| 类型            | 名称      | 描述               |
| --------------- | --------- | ------------------ |
| `System.IntPtr` | *address* | 要读取的进程的地址 |
| `<T>`           | *result*  | 结果对象           |

###### 类型参数

| 名称 | 描述         |
| ---- | ------------ |
| `T`  | 结构体的类型 |

##### Read<T>(nint, int)

从当前进程读取指定结构体的对象数组

```c#
public static T[]? Read<T>(nint address, int count) where T : struct
```

###### 返回值

`<T>[]`: 存储已读取对象的数组，如果无法读取数组的任何条目，则为 null

###### 输入值

| 类型            | 名称      | 描述               |
| --------------- | --------- | ------------------ |
| `System.IntPtr` | *address* | 要读取的进程的地址 |
| `System.Int32`  | *count*   | 数组长度           |

###### 类型参数

| 名称 | 描述         |
| ---- | ------------ |
| `T`  | 结构体的类型 |

##### Write<T>(nint, T)

为当前进程写入一个结构体

```c#
public static bool Write<T>(nint address, T obj) where T : struct
```

###### 返回值

`System.Boolean`: 写入是否成功

###### 输入值

| 类型            | 名称      | 描述               |
| --------------- | --------- | ------------------ |
| `System.IntPtr` | *address* | 要写入的进程的地址 |
| `<T>`           | *obj*     | 写入对象           |

###### 类型参数

| 名称 | 描述         |
| ---- | ------------ |
| `T`  | 结构体的类型 |

##### Write<T>(nint, T[])

为当前进程写入一个结构体数组

###### 返回值

`System.Boolean`: 写入是否成功

###### 输入值

| 类型            | 名称       | 描述               |
| --------------- | ---------- | ------------------ |
| `System.IntPtr` | *address*  | 要写入的进程的地址 |
| `<T>[]`         | *objArray* | 写入数组           |

###### 类型参数

| 名称 | 描述         |
| ---- | ------------ |
| `T`  | 结构体的类型 |

##### ReadString(nint, int)

从当前进程读取一个字符串(UTF-8)

```c#
public static string? ReadString(nint address, int maxLength = 256)
```

###### 返回值

`System.String`: 读取的字符串，当读取失败时为 null

###### 输入值

| 类型            | 名称        | 描述               |
| --------------- | ----------- | ------------------ |
| `System.IntPtr` | *address*   | 要读取的进程的地址 |
| `System.Int32`  | *maxLength* | 字符串的最大长度   |

##### ReadString(nint, Encoding, int)

从当前进程读取一个字符串(UTF-8)

```c#
public static string? ReadString(nint address, Encoding encoding, int maxLength = 256)
```

###### 返回值

`System.String`: 读取的字符串，若读取失败则为 null

###### 输入值

| 类型                   | 名称        | 描述                 |
| ---------------------- | ----------- | -------------------- |
| `System.IntPtr`        | *address*   | 要读取的进程的地址   |
| `System.Text.Encoding` | *encoding*  | 解码字符串所用的编码 |
| `System.Int32`         | *maxLength* | 字符串的最大长度     |

##### WriteString(nint, string)

为当前进程写入一个字符串

```c#
public static bool WriteString(nint address, string str)
```

###### 返回值

`System.Boolean`: 写入是否成功

###### 输入值

| 类型            | 名称      | 描述               |
| --------------- | --------- | ------------------ |
| `System.IntPtr` | *address* | 要写入的进程的地址 |
| `System.String` | *str*     | 要写入的字符串     |

##### WriteString(nint, string, Encoding)

为当前进程写入一个字符串

```c#
public static bool WriteString(nint address, string str, Encoding encoding)
```

###### 返回值

`System.Boolean`: 写入是否成功

###### 输入值

| 类型                   | 名称       | 描述                   |
| ---------------------- | ---------- | ---------------------- |
| `System.IntPtr`        | *address*  | 要写入的进程的地址     |
| `System.String`        | *str*      | 要写入的字符串         |
| `System.Text.Encoding` | *encoding* | 写入字符串所使用的编码 |

##### PtrToStructure<T>(nint)

将数据从一个非托管的内存块封送到一个托管对象

```c#
public static T? PtrToStructure<T>(nint addr) where T : struct
```

###### 返回值

`System.Nullable<<T>>`: 读取的对象，若读取失败则为 null

###### 输入值

| 类型            | 名称   | 描述               |
| --------------- | ------ | ------------------ |
| `System.IntPtr` | *addr* | 要读取的对象的地址 |

###### 类型参数

| 名称 | 描述         |
| ---- | ------------ |
| `T`  | 要创建的类型 |

##### PtrToStructure(nint, Type)

将数据从一个非托管的内存块封送到一个托管对象

```c#
public static object? PtrToStructure(nint addr, Type type)
```

###### 返回值

`System.Object`: 读取的对象，若读取失败则为 null

###### 输入值

| 类型            | 名称   | 描述               |
| --------------- | ------ | ------------------ |
| `System.IntPtr` | *addr* | 要读取的对象的地址 |
| `System.Type`   | *type* | 要创建的对象       |

##### SizeOf<T>()

获取传递类型的大小

```c#
public static int SizeOf<T>() where T : struct
```

###### 返回值

`System.Int32`: 传递类型的大小

###### 类型参数

| Name | Description  |
| ---- | ------------ |
| `T`  | 要获取的类型 |

## 枚举

### ClientLanguage

用于描述游戏加载时所使用的语言的枚举

**程序集: Dalamud.dll**

```c#
public enum ClientLanguage
```

#### 字段

##### Japanese

代表日语游戏客户端

```c#
Japanese = 0
```

##### English

代表英语游戏客户端

```c#
English = 1
```

##### German

代表德语游戏客户端

```c#
German = 2
```

##### French

代表法语游戏客户端

```c#
French = 3
```

##### ChineseSimplified

代表简体中文游戏客户端

```c#
French = 4
```

#### 扩展方法

- [Dalamud.ClientLanguageExtensions.ToLumina(Dalamud.ClientLanguage)](#ClientLanguageExtensions)
- System.Enum.Dalamud.Utility.EnumExtensions.GetAttribute
- Dalamud.Utility.EnumExtensions.IsObsolete(System.Enum) 【待补充链接】

## 委托

### EntryPoint.InitDelegate

用于 Dalamud.Boot 中 CLR 初始化期间的委托

**程序集: Dalamud.dll**

```c#
public delegate void EntryPoint.InitDelegate(nint infoPtr, nint mainThreadContinueEvent)
```

### EntryPoint.VehDelegate

CoreCLR 默认状态发生快速失败时，从 VEH 中使用的委托

**程序集: Dalamud.dll**

```c#
public delegate nint EntryPoint.VehDelegate()
```

### Localization.LocalizationChangedDelegate

Dalamud.Localization.LocalizationChanged 事件的委托，当语言改变时，事件触发

**程序集: Dalamud.dll**

```c#
public delegate nint EntryPoint.VehDelegate()
```
