---
pageClass: code-page
---

# YukiHookFactory <span class="symbol">- kt</span>

**变更记录**

`v1.0` `添加`

`v1.0.80` `修改`

合并到 `IYukiHookXposedInit`，将方法体进行 inline

**功能描述**

> 这是 `YukiHookAPI` 相关 `lambda` 方法的封装类以及部分 API 用法。

## IYukiHookXposedInit.configs <span class="symbol">- ext-method</span>

```kotlin:no-line-numbers
inline fun IYukiHookXposedInit.configs(initiate: YukiHookAPI.Configs.() -> Unit)
```

**变更记录**

`v1.0.1` `新增`

`v1.0.80` `修改`

合并到 `IYukiHookXposedInit`

**功能描述**

> 在 `IYukiHookXposedInit` 中配置 `Configs`。

## IYukiHookXposedInit.encase <span class="symbol">- ext-method</span>

```kotlin:no-line-numbers
fun IYukiHookXposedInit.encase(initiate: PackageParam.() -> Unit)
```

```kotlin:no-line-numbers
fun IYukiHookXposedInit.encase(vararg hooker: YukiBaseHooker)
```

**变更记录**

`v1.0` `添加`

`v1.0.80` `修改`

合并到 `IYukiHookXposedInit`

**功能描述**

> 在 `IYukiHookXposedInit` 中调用 `YukiHookAPI`。

## Context.modulePrefs <span class="symbol">- ext-field</span>

```kotlin:no-line-numbers
val Context.modulePrefs: YukiHookModulePrefs
```

**变更记录**

`v1.0` `添加`

**功能描述**

> 获取模块的存取对象。

## Context.modulePrefs <span class="symbol">- ext-method</span>

```kotlin:no-line-numbers
fun Context.modulePrefs(name: String): YukiHookModulePrefs
```

**变更记录**

`v1.0` `添加`

**功能描述**

> 获取模块的存取对象，可设置 `name` 为自定义 Sp 存储名称。

## Context.dataChannel <span class="symbol">- ext-method</span>

```kotlin:no-line-numbers
fun Context.dataChannel(packageName: String): YukiHookDataChannel.NameSpace
```

**变更记录**

`v1.0.88` `新增`

**功能描述**

> 获取模块的数据通讯桥命名空间对象。

::: danger

只能在模块环境使用此功能，其它环境下使用将不起作用。

:::

## Context.processName <span class="symbol">- ext-field</span>

```kotlin:no-line-numbers
val Context.processName: String
```

**变更记录**

`v1.0` `添加`

**功能描述**

> 获取当前进程名称。

## Context+Resources.injectModuleAppResources <span class="symbol">- ext-method</span>

```kotlin:no-line-numbers
fun Context.injectModuleAppResources()
```

```kotlin:no-line-numbers
fun Resources.injectModuleAppResources()
```

**变更记录**

`v1.1.0` `新增`

**功能描述**

> 向 Hook APP (宿主) `Context` 或 `Resources` 注入当前 Xposed 模块的资源。

注入成功后，你就可以直接使用例如 `ImageView.setImageResource` 或 `Resources.getString` 装载当前 Xposed 模块的资源 ID。

注入的资源作用域仅限当前 `Context` 或 `Resources`，你需要在每个用到宿主 `Context` 或 `Resources` 的地方重复调用此方法进行注入才能使用。

::: danger

只能在 (Xposed) 宿主环境使用此功能，其它环境下使用将不生效且会打印警告信息。

:::

## Context.registerModuleAppActivities <span class="symbol">- ext-method</span>

```kotlin:no-line-numbers
fun Context.registerModuleAppActivities(proxy: Any?)
```

**变更记录**

`v1.1.0` `新增`

`v1.1.5` `修改`

加入最低 API 版本限制

**功能描述**

> 向 Hook APP (宿主) 注册当前 Xposed 模块的 `Activity`。

注册成功后，你就可以直接使用 `Context.startActivity` 来启动未在宿主中注册的 `Activity`。

使用此方法会在未注册的 `Activity` 在 Hook APP (宿主) 中启动时自动调用 `injectModuleAppResources` 注入当前 Xposed 模块的资源。

你要将需要在宿主启动的 `Activity` 继承于 `ModuleAppActivity` 或 `ModuleAppCompatActivity`。

::: danger

只能在 (Xposed) 宿主环境使用此功能，其它环境下使用将不生效且会打印警告信息。

最低支持 Android 7.0 (API 24)。

:::

## Context.applyModuleTheme <span class="symbol">- ext-method</span>

```kotlin:no-line-numbers
fun Context.applyModuleTheme(theme: Int, configuration: Configuration?): ModuleContextThemeWrapper
```

**变更记录**

`v1.1.0` `新增`

**功能描述**

> 生成一个 `ContextThemeWrapper` 代理以应用当前 Xposed 模块的主题资源。

在 Hook APP (宿主) 中使用此方法会自动调用 `injectModuleAppResources` 注入当前 Xposed 模块的资源。

如果在 Hook APP (宿主) 中使用此方法发生 `ClassCastException`，请手动设置 `configuration`。

<h2 class="deprecated">isSupportResourcesHook - field</h2>

**变更记录**

`v1.0.80` `新增`

`v1.0.91` `移除`

请转移到 `YukiHookAPI.Status.isSupportResourcesHook`

<h2 class="deprecated">isModuleActive - field</h2>

**变更记录**

`v1.0.6` `新增`

`v1.0.91` `移除`

请转移到 `YukiHookAPI.Status.isModuleActive`

<h2 class="deprecated">isXposedModuleActive - field</h2>

**变更记录**

`v1.0.6` `新增`

`v1.0.91` `移除`

请转移到 `YukiHookAPI.Status.isXposedModuleActive`

<h2 class="deprecated">isTaiChiModuleActive - field</h2>

**变更记录**

`v1.0` `添加`

`v1.0.91` `移除`

请转移到 `YukiHookAPI.Status.isTaiChiModuleActive`

<h1 class="deprecated">YukiHookModuleStatus - class</h1>

**变更记录**

`v1.0` `添加`

`v1.0.91` `作废`

请转移到 `YukiHookAPI.Status`