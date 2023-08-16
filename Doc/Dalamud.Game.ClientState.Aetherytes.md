# 命名空间: Dalamud.Game.ClientState.Aetherytes

## 类

### AetheryteEntry

该类表示以太之光传送点列表的一个以太之光条目

**程序集: Dalamud.dll**

```c#
public sealed class AetheryteEntry
```

#### 属性

##### AetheryteId

获取该以太之光的 ID

```c#
public uint AetheryteId { get; }
```

##### TerritoryId

获取该以太之光所在区域的 ID

```c#
public uint TerritoryId { get; }
```

##### SubIndex

当存在多个以太之光共享相同 ID 时 (比如个人、共享房屋)，获取其子索引

```c#
public byte SubIndex { get; }
```

##### Ward

获取所在的住宅区的区号，如果非共享房屋，该项则为0 (Gets the Ward. Zero if not a Shared Estate.) 【翻译待定】

```c#
public byte Ward { get; }
```

##### Plot

获取具体对应的地皮号数，如果非共享房屋，该项则为0 (Gets the Plot. Zero if not a Shared Estate.) 【翻译待定】

```c#
public byte Plot { get; }
```

##### GilCost

获取传送到该以太之光所要花费的金币数

```c#
public uint GilCost { get; }
```

##### IsSharedHouse

获取一个值，该值指示该以太之光是否为共享房屋

```c#
public bool IsSharedHouse { get; }
```

##### IsAppartment

获取一个值，该值指示该以太之光是否为公寓

```c#
public bool IsAppartment { get; }
```

##### AetheryteData

获取该以太之光的对应数值

```c#
public ExcelResolver<Aetheryte> AetheryteData { get; }
```

### AetheryteList

该集合表示传送窗口中可用的以太之光传送点列表

**程序集: Dalamud.dll**

```c#
public sealed class AetheryteList : IServiceType, IAetheryteList, IReadOnlyCollection<AetheryteEntry>, IEnumerable<AetheryteEntry>, IEnumerable
```

**实现:**
[Dalamud.IServiceType](Dalamud.md#IServiceType), Dalamud.Plugin.Services.IAetheryteList 【待补充链接】, `System.Collections.Generic.IReadOnlyCollection<Dalamud.Game.ClientState.Aetherytes.AetheryteEntry>`, `System.Collections.Generic.IEnumerable<Dalamud.Game.ClientState.Aetherytes.AetheryteEntry>`, `System.Collections.IEnumerable`

#### 属性

##### Length

获取本地玩家已解锁的以太之光数量

```c#
public int Length { get; }
```

##### this[int]

根据给定的索引位置获取一个特定的以太之光

```c#
public AetheryteEntry? this[int index] { get; }
```

##### Count

获取该集合内元素的数量 (Gets the number of elements in the collection) 【翻译待定】 

```c#
public int Count { get; }
```

#### 方法

##### GetEnumerator()

返回一个用于遍历该集合中元素的枚举器

```c#
public IEnumerator<AetheryteEntry> GetEnumerator()
```

###### 返回值

`System.Collections.Generic.IEnumerator<Dalamud.Game.ClientState.Aetherytes.AetheryteEntry>`:一个用于遍历该集合中元素的枚举器

#### 实现

- [Dalamud.IServiceType](Dalamud.md#IServiceType)
- Dalamud.Plugin.Services.IAetheryteList 【链接待补充】
- `System.Collections.Generic.IReadOnlyCollection<Dalamud.Game.ClientState.Aetherytes.AetheryteEntry>`
- `System.Collections.Generic.IEnumerable<Dalamud.Game.ClientState.Aetherytes.AetheryteEntry>`
- `System.Collections.IEnumerable`