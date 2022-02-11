---
title: 教程：一个最小的示例 | tutorial-A Minimal Example
date: 2022-01-30 18:04:16
categories:
- SV - Scripting
- Tutorial
tags:
- SynthV
- Scripting
- Example
---

## 一个最小示例

最小工作脚本由两个全局函数组成： `getClientInfo()` 和 `main()`。

<!-- more -->

`getClientInfo()`在宿主加载脚本时调用。它返回一个对象，该对象描述脚本的名称，作者，版本以及运行脚本所需的Synthesizer V Studio的最小版本号。
`main()`在用户执行脚本时调用。

---

### Example (JavaScript)

``` js 
function getClientInfo() {
  return {
    "name" : "My Script",
    "category" : "Example",
    "author" : "Bob Alice",
    "versionNumber" : 1,
    "minEditorVersion" : 65540
  };
}

function main() {
  SV.showMessageBox("My Script", "Hello, world!");
  SV.finish();
}
```

### Example (Lua)

``` lua
function getClientInfo()
  return {
    name = "My Script",
    category = "Example",
    author = "Bob Alice",
    versionNumber = 1,
    minEditorVersion = 65540
  }
end

function main()
  SV:showMessageBox("My Script", "Hello, world!")
  SV:finish()
end
```