# flash-zh.nvim

> [!NOTE]
> 這是 [rainzm/flash-zh.nvim](https://github.com/rainzm/flash-zh.nvim) 的 fork，
> 將 `flypy.lua` 的簡體中文字典使用 opencc 轉換成繁體中文，主要程式實作來自於 flash-zh.nvim 與 flash.nvim

基于[flash.nvim](https://github.com/folke/flash.nvim)以及小鹤双拼，neovim 中文跳转插件。

![iShot_2023-10-05_19 32 53](https://github.com/rainzm/flash-zh.nvim/assets/22927169/4c3ca124-0fee-48a2-b7c6-17391afe8d0e)

## 安装

- 依赖于[flash.nvim](https://github.com/folke/flash.nvim)
- 使用 [lazy.nvim](https://github.com/folke/lazy.nvim) 进行安装:

```lua
return {{
    "rainzm/flash-zh.nvim",
    event = "VeryLazy",
    dependencies = "folke/flash.nvim",
    keys = {{
        "s",
        mode = {"n", "x", "o"},
        function()
            require("flash-zh").jump({
                chinese_only = false
            })
        end,
        desc = "Flash between Chinese"
    }}
}, {
    "folke/flash.nvim",
    event = "VeryLazy",
    opts = {
        highlight = {
            backdrop = false,
            matches = false
        }
    }
}}
```

## 使用

1. ~~label 默认使用大写字母，这样可以避免和拼音冲突。~~ label 现在默认使用小写字母，通过自定义`flash.nvim`的 labeler ，以避免小写 label 和拼音的冲突。
2. 默认工作在中英混杂模式下（由[dirichy](https://github.com/dirichy)实现）；增加选项 `chinese_only` 使其工作在仅中文模式下。
3. `jump`的参数会传递给`flash.nvim`，查看 [issue 2](https://github.com/rainzm/flash-zh.nvim/issues/2) 。

**如果想要跳转的地方没有 label 出现，接着输入即可，和查找一样。**

## 感谢

- [hop-zh-by-flypy](https://github.com/zzhirong/hop-zh-by-flypy)

## 推荐

- [rime-ls](https://github.com/wlh320/rime-ls) 通过补全的方式输入中文
