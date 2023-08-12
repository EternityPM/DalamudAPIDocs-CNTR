# 命名空间: Dalamud.Configuration

## 类

### PluginConfigurations

用于存储一个 Dalamud 插件设置的配置

**程序集: Dalamud.dll**

```c#
public sealed class PluginConfigurations
```

#### 方法

##### Save(IPluginConfiguration, string)

保存/加载插件配置

注意: 尽管 LoadForType 已经取代了 Load，并且其已经不再需要或者使用 类型信息，但 Save/Load 目前仍在使用类型信息。也许值得从 Save 中移除类型信息，以便从未来的所有保存的配置中去除它，然后 Load 方法也许就能完全被移除了

###### 输入值

| 类型                                                         | 名称         | 描述     |
| ------------------------------------------------------------ | ------------ | -------- |
| [Dalamud.Configuration.IPluginConfiguration](#IPluginConfiguration) | *config*     | 插件配置 |
| `System.String`                                              | *pluginName* | 插件名称 |

##### Load(string)

加载插件配置

```c#
public IPluginConfiguration? Load(string pluginName)
```

###### 返回值

[Dalamud.Configuration.IPluginConfiguration](#IPluginConfiguration): 插件配置

###### 输入值

| 类型            | 名称         | 描述     |
| --------------- | ------------ | -------- |
| `System.String` | *pluginName* | 插件名称 |

##### Delete(string)

删除指定插件的配置文件和配置文件夹。如果插件没有正确关闭其自身的句柄时，则会扔出`System.IO.IOException`

```c#
public void Delete(string pluginName)
```

###### 输入值

| 类型            | 名称         | 描述     |
| --------------- | ------------ | -------- |
| `System.String` | *pluginName* | 插件名称 |

##### GetDirectory(string)

获取插件目录

```c#
public string GetDirectory(string pluginName)
```

###### 返回值

`System.String`: 插件目录路径

###### 输入值

| 类型            | 名称         | 描述     |
| --------------- | ------------ | -------- |
| `System.String` | *pluginName* | 插件名称 |

##### LoadForType<T>(string)

加载插件配置。使用参数控制反序列化。目前通过反射从 DalamudPluginInterface.GetPluginConfig() 调用此方法。最终可能会有一个额外的 pluginInterface 方法，以便直接调用而无需反射 —— 目前是为了支持现有的插件 API 而为之

```c#
public T LoadForType<T>(string pluginName) where T : IPluginConfiguration
```

###### 返回值

`<T>`: 插件配置

###### 输入值

| 类型            | 名称         | 描述     |
| --------------- | ------------ | -------- |
| `System.String` | *pluginName* | 插件名称 |

###### 类型参数

| 名称 | 描述     |
| ---- | -------- |
| `T`  | 配置类型 |

##### GetConfigFile(string)

获取插件配置文件的文件信息

```c#
public FileInfo GetConfigFile(string pluginName)
```

###### 返回值

`System.IO.FileInfo`: 配置文件的文件信息

###### 输入值

| 类型            | 名称         | 描述     |
| --------------- | ------------ | -------- |
| `System.String` | *pluginName* | 插件名称 |

## 接口

### IPluginConfiguration

用于存储一个 Dalamud 插件设置的配置

**程序集: Dalamud.dll**

```c#
public interface IPluginConfiguration
```

#### 属性

##### Version

获取或设置配置版本

```c#
int Version { get; set; }
```

