---
title: 轨道 | Track
date: 2022-01-30 17:27:22
categories:
- SV - Scripting 
- Classes
tags:
- Track
- SynthV
- Scripting
---

轨道 (Track) 是 [音符组引用](../NoteGroupReference) 的集合。一个 `轨道` 也包括了 [音符组](../NoteGroup) ，它是轨道的主要组。轨道内的第一个 [音符组引用](../NoteGroupReference) 始终指向主要组。

<!-- more -->

`轨道` 默认的声库属性由第一个 [音符组引用](../NoteGroupReference) 决定（即主要组）。

## 扩展

* [嵌套对象](../NestedObject)

## 方法

{% note info %}
### addGroupReference(group) → {number}
{% endnote %}

向该 `轨道` 添加一个 [音符组引用](../NoteGroupReference) ，并返回添加组的索引。它按照起始位置对所有组进行排序。

#### 参数

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| `group` | [音符组引用](../NoteGroupReference) |  |

#### 返回

类型：数

---

{% note info %}
### clone() → {[Track](../Track)}
{% endnote %}

深复制当前对象。

#### 返回

类型：[轨道](../Track)

---

{% note info %}
### getDisplayColor() → {string}
{% endnote %}

获得轨道的颜色（十六进制字符串）

#### 返回

类型：字符串

---

{% note info %}
### getDisplayOrder() → {number}
{% endnote %}

获取父 [工程](../Project) 中轨道的显示顺序。轨道的显示顺序可以与其储存的索引不同。在编曲区界面中显示的轨道顺序总是基于显示顺序。
#### 返回

类型：数

---

{% note info %}
### getDuration() → {number}
{% endnote %}

获取 `轨道` 的持续时间，被定义为最后一个 [音符组引用](../NoteGroupReference) 结束的位置，以块 (blicks) 为单位，

#### 返回

类型：数

---

{% note info %}
### getGroupReference(index) → {[NoteGroupReference](../NoteGroupReference)}
{% endnote %}

获取第 `index` 个 [音符组引用](../NoteGroupReference) 索引。第一个是主组，后跟项目库中引用了 [音符组](../NoteGroup)的组。这些组按起始位置升序排序。

#### 参数

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| `index` | number | |


#### 返回

类型：[音符组引用](../NoteGroupReference)

---

{% note info %}
### getIndexInParent() → {number}
{% endnote %}

> 继承自：[嵌套对象 - `getIndexInParent`](../NestedObject#getParent)

获取当前对象在其父对象中的索引。 在 Lua 中，这个索引从 1 开始。在 JavaScript 中，这个索引从 0 开始。
#### 返回

类型：数

---

{% note info %}
### getName() → {string}
{% endnote %}

获得轨道名称。

#### 返回

类型：字符串

---

{% note info %}
### getNumGroups() → {number}
{% endnote %}

获取该 `轨道` 中的 [音符组引用](../NoteGroupReference) 的数量，包括主要组。

#### 返回

类型：数

---

{% note info %}
### getParent() → {[NestedObject](../NestedObject)|undefined}
{% endnote %}

> 继承自：[嵌套对象 - `getParent`](../NestedObject#getParent)

获取父 [嵌套对象](../NestedObject) 。如果当前对象未附加到父对象，则返回 `undefined` 。

#### 返回

类型：[嵌套对象](../NestedObject) | `undefined`

---
{% note info %}
### isBounced() → {boolean}
{% endnote %}

用于决定是否导出到文件，它显示在"渲染面板 - 音轨"中。

#### 返回

类型：布尔

---

{% note info %}
### isMemoryManaged() → {boolean}
{% endnote %}

> 继承自：[嵌套对象 - `isMemoryManaged`](../NestedObject#isMemoryManaged)

检测选中的对象是否被内存管理（即脚本环境的垃圾回收）。

#### 返回

类型：布尔

---

{% note info %}
### removeGroupReference(index)
{% endnote %}

从 `轨道` 中移除第 `index` 个 [音符组引用](../NoteGroupReference) 。

#### 参数

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| `index` | number |  |

---
{% note info %}
### setBounced(enabled)
{% endnote %}

设置是否将 `轨道` 导出到文件。请参阅 [轨道 - `isBounced`](../Track)。

#### 参数

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| `enabled` | boolean | |

---

{% note info %}
### setDisplayColor(colorStr)
{% endnote %}

设置 `轨道` 的显示颜色。（十六进制字符串）

#### 参数

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| `colorStr` | string |  |
---
{% note info %}
### setName(name)
{% endnote %}

设置当前 `轨道` 的名称。

#### 参数

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| `name` | string |  |

