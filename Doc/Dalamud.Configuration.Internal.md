# 命名空间: Dalamud.Configuration.Internal

## 类

### PluginTestingOptIn

**程序集: Dalamud.dll**

```c#
public record PluginTestingOptIn : IEquatable<PluginTestingOptIn>
```

**实现:**

`System.IEquatable<Dalamud.Configuration.Internal.PluginTestingOptIn>`

#### 属性

##### InternalName

获取要测试的插件的内部名称

```c#
public string InternalName { get; }
```

##### Branch

获取要使用的测试分支

```c#
public string Branch { get; }
```

#### 实现

- `System.IEquatable<Dalamud.Configuration.Internal.PluginTestingOptIn>`
