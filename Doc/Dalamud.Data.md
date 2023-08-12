# 命名空间: Dalamud.Data

## 类

### DataManager

该类为 Dalamud 内部的功能提供数据，但也可以在有需要时被插件调用

程序集: **Dalamud.dll**

```c#
public sealed class DataManager : IDisposable, IServiceType, IDataManager
```

**实现**

`System.IDisposable`, [Dalamud.IServiceType](Dalamud.md#IServiceType), Dalamud.Plugin.Services.IDataManager 【待添加链接】

#### 属性

##### Language

获取当前游戏客户端的语言

```c#
public ClientLanguage Language { get; }
```

##### ServerOpCodes

获取服务器发送到客户端的 OpCodes

```c#
public ReadOnlyDictionary<string, ushort> ServerOpCodes { get; }
```

##### ClientOpCodes

获取客户端发送到服务器的 OpCodes

```c#
[UsedImplicitly]
public ReadOnlyDictionary<string, ushort> ClientOpCodes { get; }
```

##### GameData

获取一个用于访问任意 Excel/游戏数据的 `Lumina` 对象

```c#
public GameData GameData { get; }
```

##### Excel

获取一个用于访问游戏内任意表格数据的 `Lumina.Excel.ExcelModule` 对象

```c#
public ExcelModule Excel { get; }
```

##### IsDataReady

获取一个值，该值指示游戏数据是否已准备好被读取

```c#
public bool IsDataReady { get; }
```

##### HasModifiedGameDataFiles

获取一个值，该值指示游戏数据是否已被其他第三方工具所修改

```c#
public bool HasModifiedGameDataFiles { get; }
```

#### 方法

##### GetExcelSheet<T>()

获取一个具有给定 Excel 表格行类型的 `Lumina.Excel.ExcelSheet<T>`

```c#
public ExcelSheet<T>? GetExcelSheet<T>() where T : ExcelRow
```

###### 返回值：

`Lumina.Excel.ExcelSheet<T>`：提供对游戏行的访问

###### 类型参数

| 名称 | 描述                     |
| ---- | ------------------------ |
| `T`  | 要获取的 Excel 表格类型 |

##### GetExcelSheet<T>(ClientLanguage)

获取一个使用特定语言的、具有给定 Excel 表格行类型的 `Lumina.Excel.ExcelSheet<T>`

```c#
public ExcelSheet<T>? GetExcelSheet<T>(ClientLanguage language) where T : ExcelRow
```

###### 返回值

`Lumina.Excel.ExcelSheet<T>`: 提供对游戏行的访问

###### 输入值

| 类型                  | 名称     | 描述           |
| --------------------- | -------- | -------------- |
| [Dalamud.ClientLanguage](Dalamud.md#ClientLanguage) | *language* | 要获取的表格的语言 |

###### 类型参数

| 名称 | 描述                     |
| ---- | ------------------------ |
| `T`  | 要获取的 Excel 表格类型。 |

##### GetFile(string)

从给定路径获取一个 `Lumina.Data.FileResource`

```c#
public FileResource? GetFile(string path)
```

###### 返回值

`Lumina.Data.FileResource`: 文件的 `Lumina.Data.FileResource` 资源

###### 传入值

| 类型         | 名称 | 描述             |
| ------------ | ---- | ---------------- |
| `System.String` | *path* | 游戏文件中的内部路径 |

##### GetFile<T>(string)

从给定路径获取一个指定类型的 `Lumina.Data.FileResource`

```c#
public T? GetFile<T>(string path) where T : FileResource
```

###### 返回值

`<T>`: 文件的 `Lumina.Data.FileResource` 资源

###### 传入值

| 类型         | 名称 | 描述             |
| ------------ | ---- | ---------------- |
| `System.String` | *path* | 游戏文件中的内部路径 |

###### 类型参数

| 名称 | 描述             |
| ---- | ---------------- |
| `T`  | 资源类型。 |

##### FileExists(string)

从给定路径检查其中文件是否存在于游戏的索引文件中

```c#
public bool FileExists(string path)
```

###### 返回值

`System.Boolean`: 若文件存在则为 true

###### 参数

| 类型         | 名称 | 描述             |
| ------------ | ---- | ---------------- |
| `System.String` | *path* | 游戏文件中的内部路径 |

##### GetIcon(uint)

获取给定 ID 的图标的 `Lumina.Data.Files.TexFile`

```c#
public TexFile? GetIcon(uint iconId)
```

###### 返回值

`Lumina.Data.Files.TexFile`: 包含图标的 `Lumina.Data.Files.TexFile`

###### 传入值

| 类型        | 名称     | 描述   |
| ----------- | -------- | ------ |
| `System.UInt32` | *iconId* | 图标 ID |

##### GetIcon(uint, bool)

获取给定 ID 的图标的 `Lumina.Data.Files.TexFile`

```c#
public TexFile? GetIcon(uint iconId, bool highResolution)
```

###### 返回值

`Lumina.Data.Files.TexFile`: 包含图标的 `Lumina.Data.Files.TexFile`

###### 参数

| 类型        | 名称             | 描述                   |
| ----------- | ---------------- | ---------------------- |
| `System.UInt32` | *iconId*       | 图标 ID             |
| `System.Boolean` | *highResolution* | 是否返回高分辨率版本 |

##### GetIcon(bool, uint)

获取给定 ID 的指定物品质量的图标的 `Lumina.Data.Files.TexFile`

```c#
public TexFile? GetIcon(bool isHq, uint iconId)
```

###### 返回值

`Lumina.Data.Files.TexFile`: 包含图标的 `Lumina.Data.Files.TexFile`

###### 传入值

| 类型        | 名称    | 描述                 |
| ----------- | ------- | -------------------- |
| `System.Boolean` | *isHq* | 是否返回 HQ 版本 |
| `System.UInt32` | *iconId* | 图标 ID      |

##### GetIcon(ClientLanguage, uint)

获取给定 ID 的指定语言的图标的 `Lumina.Data.Files.TexFile`

```c#
public TexFile? GetIcon(ClientLanguage iconLanguage, uint iconId)
```

###### 返回值

`Lumina.Data.Files.TexFile`: 包含图标的 `Lumina.Data.Files.TexFile`

###### 传入值

| 类型                  | 名称         | 描述               |
| --------------------- | ------------ | ------------------ |
| [Dalamud.ClientLanguage](Dalamud.md#ClientLanguage) | *iconLanguage* | 图标语言    |
| `System.UInt32` | *iconId*   | 图标 ID。         |

##### GetIcon(ClientLanguage, uint, bool)

获取给定 ID 的指定语言的图标的 `Lumina.Data.Files.TexFile`

```c#
public TexFile? GetIcon(ClientLanguage iconLanguage, uint iconId, bool highResolution)
```

###### 返回值

`Lumina.Data.Files.TexFile`: 包含图标的 `Lumina.Data.Files.TexFile`

###### 传入值

| 类型                                                | 名称             | 描述                 |
| --------------------------------------------------- | ---------------- | -------------------- |
| [Dalamud.ClientLanguage](Dalamud.md#ClientLanguage) | *iconLanguage*   | 图标语言             |
| `System.UInt32`                                     | *iconId*         | 图标 ID              |
| `System.Boolean`                                    | *highResolution* | 是否返回高分辨率版本 |

##### GetIcon(string?, uint)

获取给定 ID 的指定类型的图标的 `Lumina.Data.Files.TexFile`

```c#
public TexFile? GetIcon(string? type, uint iconId)
```

###### 返回值

`Lumina.Data.Files.TexFile`: 包含图标的 `Lumina.Data.Files.TexFile`

###### 传入值

| 类型         | 名称  | 描述                                           |
| ------------ | ----- | ---------------------------------------------- |
| `System.String` | *type* | 图标类型(如: 传入 "hq" 以获取图标的 HQ 版本) |
| `System.UInt32` | *iconId* | 图标 ID                                     |

##### GetIcon(string?, uint, bool)

获取给定 ID 的指定类型的图标的 `Lumina.Data.Files.TexFile`

```c#
public TexFile? GetIcon(string? type, uint iconId, bool highResolution)
```

###### 返回值

`Lumina.Data.Files.TexFile`: 包含图标的 `Lumina.Data.Files.TexFile`

###### 传入值

| 类型         | 名称             | 描述                                           |
| ------------ | ---------------- | ---------------------------------------------- |
| `System.String` | *type*           | 图标类型(如: 传入 "hq" 以获取图标的 HQ 版本) |
| `System.UInt32` | *iconId*         | 图标 ID                           |
| `System.Boolean` | *highResolution* | 是否返回高分辨率版本                 |

##### GetHqIcon(uint)

获取给定 ID 的 HQ 图标的 `Lumina.Data.Files.TexFile`

```c#
public TexFile? GetHqIcon(uint iconId)
```

###### 返回值

`Lumina.Data.Files.TexFile`: 包含图标的 `Lumina.Data.Files.TexFile`

###### 传入值

| 类型        | 名称     | 描述   |
| ----------- | -------- | ------ |
| `System.UInt32` | *iconId* | 图标 ID |

##### GetImGuiTexture(TexFile?)

将传递的 `Lumina.Data.Files.TexFile` 获取为可被绘制的 ImGui TextureWrap

```c#
public TextureWrap? GetImGuiTexture(TexFile? tex)
```

###### 返回值

ImGuiScene.TextureWrap 【待补充链接】: 可用于  ImGuiScene.TextureWrap【待补充链接】 绘制纹理

###### 传入值

| 类型                         | 名称 | 描述               |
| ---------------------------- | ---- | ------------------ |
| `Lumina.Data.Files.TexFile` | *tex* | `Lumina.Data.Files.TexFile`数据文件 |

##### GetImGuiTexture(string)

从传递的纹理路径获取可被绘制的 ImGui TextureWrap

```c#
public TextureWrap? GetImGuiTexture(string path)
```

###### 返回值

ImGuiScene.TextureWrap 【待补充链接】: 可用于  ImGuiScene.TextureWrap【待补充链接】 绘制纹理

###### 传入值

| 类型         | 名称 | 描述                     |
| ------------ | ---- | ------------------------ |
| `System.String` | *path* | 纹理的内部路径 |

##### GetImGuiTextureIcon(uint)

获取给定 ID 的图标的 ImGuiScene.TextureWrap 【待补充链接】

```c#
public TextureWrap? GetImGuiTextureIcon(uint iconId)
```

###### 返回值

ImGuiScene.TextureWrap 【待补充链接】: 包含图标的 ImGuiScene.TextureWrap【待补充链接】

###### 传入值

| 类型        | 名称     | 描述   |
| ----------- | -------- | ------ |
| `System.UInt32` | *iconId* | 图标 ID |

##### GetImGuiTextureIcon(uint, bool)

获取给定 ID 的图标的 ImGuiScene.TextureWrap 【待补充链接】

```c#
public TextureWrap? GetImGuiTextureIcon(uint iconId, bool highResolution)
```

###### 返回值

ImGuiScene.TextureWrap 【待补充链接】: 包含图标的 ImGuiScene.TextureWrap【待补充链接】

###### 传入值

| 类型        | 名称             | 描述                   |
| ----------- | ---------------- | ---------------------- |
| `System.UInt32` | *iconId*       | 图标 ID             |
| `System.Boolean` | *highResolution* | 是否返回高分辨率版本 |

##### GetImGuiTextureIcon(bool, uint)

获取给定 ID 的图标的 ImGuiScene.TextureWrap 【待补充链接】

```c#
public TextureWrap? GetImGuiTextureIcon(bool isHq, uint iconId)
```

###### 返回值

ImGuiScene.TextureWrap 【待补充链接】: 包含图标的 ImGuiScene.TextureWrap【待补充链接】

###### 传入值

| 类型        | 名称    | 描述                 |
| ----------- | ------- | -------------------- |
| `System.Boolean` | *isHq* | 是否返回 HQ 版本 |
| `System.UInt32` | *iconId* | 图标 ID           |

##### GetImGuiTextureIcon(ClientLanguage, uint)

获取给定 ID 的图标的 ImGuiScene.TextureWrap 【待补充链接】

```c#
public TextureWrap? GetImGuiTextureIcon(ClientLanguage iconLanguage, uint iconId)
```

###### 返回值

ImGuiScene.TextureWrap 【待补充链接】: 包含图标的 ImGuiScene.TextureWrap【待补充链接】

###### 传入值

| 类型                  | 名称         | 描述               |
| --------------------- | ------------ | ------------------ |
| [Dalamud.ClientLanguage](Dalamud.md#ClientLanguage) | *iconLanguage* | 图标语言     |
| `System.UInt32` | *iconId*   | 图标 ID         |

##### GetImGuiTextureIcon(string, uint)

获取给定 ID 的图标的 ImGuiScene.TextureWrap 【待补充链接】

```c#
public TextureWrap? GetImGuiTextureIcon(string type, uint iconId)
```

###### 返回值

ImGuiScene.TextureWrap 【待补充链接】: 包含图标的 ImGuiScene.TextureWrap【待补充链接】

###### 传入值

| 类型         | 名称  | 描述                                           |
| ------------ | ----- | ---------------------------------------------- |
| `System.String` | *type* | 图标类型(如: 传入 "hq" 以获取图标的 HQ 版本) |
| System.UInt32 | *iconId* | 图标 ID                                     |

##### GetImGuiTextureHqIcon(uint)

获取给定 ID 的 HQ 图标的 ImGuiScene.TextureWrap 【待补充链接】

```c#
public TextureWrap? GetImGuiTextureHqIcon(uint iconId)
```

###### 返回值

ImGuiScene.TextureWrap 【待补充链接】: 包含图标的 ImGuiScene.TextureWrap【待补充链接】

###### 传入值

| 类型        | 名称     | 描述   |
| ----------- | -------- | ------ |
| `System.UInt32` | *iconId* | 图标 ID |
#### 实现

- `System.IDisposable`
- [Dalamud.IServiceType](Dalamud.md#IServiceType)
- Dalamud.Plugin.Services.IDataManager 【待补充链接】