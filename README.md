# SD ↔ NAI Prompt 转换器

一个纯前端的单文件工具，用于在 Stable Diffusion 与 NovelAI 两种 Prompt 语法之间互相转换。

打开 [index.html](./index.html) 即可使用，无需任何依赖与服务端。

## 功能

- **双向转换**
  - SD `(text:1.2)` / `((text))` / `[text]` ↔ NAI 经典 `{{text}}` / `[text]`
  - SD `(text:1.5)` ↔ NAI v4 `1.5::text::`
- **权重换算**：`{}` 每层 ×1.05，`()` 默认 ×1.1，`[]` ×(1/1.1)，嵌套自动叠乘
- **SD 权重形式可切换**：`(t:1.16)` 数值形式 或 `((t))` 括号堆叠形式
- **NAI 格式可切换**：经典 `{{}}` 或 v4 `weight::text::`
- **中文括号识别**：`（text）` 自动识别为权重括号
- **空格 / 下划线**：转换为 NAI v4 时默认把空格转为 `_`，可通过「保留空格」开关关闭
- **自动识别方向**：贴进任一框都能识别，按一键转换即可
- **快捷键**
  - `Ctrl + Enter` 执行转换
  - `Ctrl + Shift + C` 复制结果

## 使用

```
git clone https://github.com/StingGrey/sd-nai-transform.git
```

或直接下载 [index.html](./index.html)，双击在浏览器中打开。

## 权重换算参考

| 写法 | 倍率 |
|---|---|
| `{text}` | ×1.05 |
| `{{text}}` | ×1.1025 |
| `{{{text}}}` | ×1.1576 |
| `[text]` | ×0.9524 |
| `(text)` | ×1.1 |
| `((text))` | ×1.21 |
| `(text:1.2)` | ×1.2 |

## 致谢

灵感与权重规则参考自 [sudoskys/sd-nai-](https://github.com/sudoskys/sd-nai-)。

## License

Apache-2.0
