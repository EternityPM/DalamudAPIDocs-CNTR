# 命名空间: Dalamud.Game.ClientState.Buddy

## 类

### BuddyList

该集合代表你的伙伴们(如: 专属陆行鸟、宠物、冒险者分队、亲信战友)，不包含玩家自身

**程序集：Dalamud.dll**

```c#
public sealed class BuddyList : IServiceType, IBuddyList, IReadOnlyCollection<BuddyMember>, IEnumerable<BuddyMember>, IEnumerable
```

#### 属性

##### Length

获取本地玩家的战斗伙伴数量

```c#
public int Length { get; }
```

##### CompanionBuddyPresent

获取一个值，该值指示本地玩家的搭档(专属陆行鸟)是否在场

```c#
[Obsolete("Use CompanionBuddy != null", false)]
public bool CompanionBuddyPresent { get; }
```

##### PetBuddyPresent

获取一个值，该值指示本地玩家的宠物是否在场

```c#
[Obsolete("Use PetBuddy != null", false)]
public bool PetBuddyPresent { get; }
```

##### CompanionBuddy

获取当前召唤的搭档

```c#
public BuddyMember? CompanionBuddy { get; }
```

##### PetBuddy

获取当前激活的宠物

```c#
public BuddyMember? PetBuddy { get; }
```

##### this[int]

获取给定召唤索引处的战斗伙伴 (Gets a battle buddy at the specified spawn index.) 【翻译待定】

```c#
public BuddyMember? this[int index] { get; }
```

#### 方法

##### GetCompanionBuddyMemberAddress()

获取搭档的内存地址

```c#
public nint GetCompanionBuddyMemberAddress()
```

###### 返回值

`System.IntPtr`: 搭档的内存地址

##### GetPetBuddyMemberAddress()

获取宠物的内存地址

```c#
public nint GetPetBuddyMemberAddress()
```

###### 返回值

`System.IntPtr`: 宠物的内存地址

##### GetBattleBuddyMemberAddress(int)

获取给定索引处的战斗伙伴在伙伴列表中的内存地址

```c#
public nint GetBattleBuddyMemberAddress(int index)
```

###### 返回值

System.IntPtr`: 战斗伙伴的内存地址

###### 输入值

| 类型           | 名称   | 描述           |
| -------------- | ------ | -------------- |
| `System.Int32` | *index* | 战斗伙伴的索引 |

##### CreateBuddyMemberReference(nint)

创建一个对伙伴的引用。

```c#
public BuddyMember? CreateBuddyMemberReference(nint address)
```

###### 返回值

`Dalamud.Game.ClientState.Buddy.BuddyMember`: 一个包含所请求数据的伙伴对象

输入值：

| 类型             | 名称     | 描述           |
| ---------------- | -------- | -------------- |
| `System.IntPtr`  | *address* | 伙伴的内存地址 |

##### GetEnumerator()

返回一个用于遍历集合的枚举器

```c#
public IEnumerator<BuddyMember> GetEnumerator()
```

###### 返回值

`System.Collections.Generic.IEnumerator<Dalamud.Game.ClientState.Buddy.BuddyMember>`: 可用于遍历集合的枚举器

#### 实现

- [Dalamud.IServiceType](Dalamud.md#IServiceType)
- Dalamud.Plugin.Services.IBuddyList 【链接待补充】
- `System.Collections.Generic.IReadOnlyCollection<Dalamud.Game.ClientState.Buddy.BuddyMember>`
- `System.Collections.Generic.IEnumerable<Dalamud.Game.ClientState.Buddy.BuddyMember>`
- `System.Collections.IEnumerable`

### BuddyMember

该集合代表了一位伙伴(如: 专属陆行鸟、宠物、冒险者分队、亲信战友)

**程序集: Dalamud.dll**

```c#
public class BuddyMember
```

#### 属性

##### Address

获取伙伴在内存中的地址

```c#
public nint Address { get; }
```

##### ObjectId

获取该伙伴的对象ID

```c#
public uint ObjectId { get; }
```

##### GameObject

获取与该伙伴相关联的角色对象

```c#
public GameObject? GameObject { get; }
```

##### CurrentHP

获取该伙伴的当前生命值

```c#
public uint CurrentHP { get; }
```

##### MaxHP

获取该伙伴的最大生命值

```c#
public uint MaxHP { get; }
```

##### DataID

获取该伙伴的数据 ID

```c#
public uint DataID { get; }
```

##### MountData

获取与该伙伴相关的坐骑数据，只适用于专属陆行鸟

```c#
public ExcelResolver<Mount> MountData { get; }
```

##### PetData

获取与该伙伴相关的宠物数据，只适用于宠物

```c#
public ExcelResolver<Pet> PetData { get; }
```

##### TrustData

获取与该伙伴相关的信任数据，只适用于战斗伙伴(亲信战友、冒险者小队)等

```c#
public ExcelResolver<DawnGrowMember> TrustData { get; }
```