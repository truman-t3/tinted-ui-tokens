# tinted-ui-tokens

> A WorkBuddy skill that generates a complete, production-ready **brand-tinted design-token system** from a single brand color.
> 一个 WorkBuddy 技能：输入一个品牌色，自动生成一套完整、可直接上线的「染色中性色」设计 Token 系统。

No pure neutral colors anywhere (`#FFFFFF`, `#000000`, `#808080`): every surface, border, text, shadow, semantic color, gradient, and icon picks up a few percent of the brand's temperature.
任何地方都不使用纯中性色（`#FFFFFF`、`#000000`、`#808080`）：每一个背景、表面、边框、文字、阴影、语义色、渐变与图标，都带上一小撮品牌色的温度。

---

## What it does · 它能做什么

- **Input · 输入：** one brand color (hex) + optional name / style · 一个品牌色（hex）＋ 可选的名称 / 风格
- **Output · 输出：** `tokens.css` (`:root` + `[data-theme="dark"]`) and a self-contained `preview.html` · `tokens.css`（含 `:root` 与 `[data-theme="dark"]`）以及一份自包含的 `preview.html`
- **Covers · 覆盖：** backgrounds, surfaces, borders, text hierarchy, shadows, semantic colors (error / warning / success nudged toward the brand's temperature), gradients, icons, and dark mode · 背景、表面、边框、文字层级、阴影、语义色（错误 / 警告 / 成功，被轻推至品牌色温）、渐变、图标，以及深色模式

## Usage · 使用方法

Invoke the skill inside WorkBuddy. Say something like:
在 WorkBuddy 中唤起该技能，像这样说：

> 用 `#2563EB` 出一套染色 Token 系统

and it runs `scripts/generate_tokens.py` to produce the files.
它会运行 `scripts/generate_tokens.py` 来生成这些文件。

Command-line equivalent · 等效命令行：

```bash
python scripts/generate_tokens.py --brand "#2563EB" --name "Acme" --out "./out"
```

## How it works · 工作原理

The generator is **brand-agnostic**: it mixes the brand hue into a neutral ramp with a small chroma, derives a warm / cool / balanced temperature, and emits a full token set — instead of hard-coding the two palettes from the article.
生成器是**品牌无关**的：它把品牌色相以极小的彩度混入中性色阶，推导出暖 / 冷 / 中性三种温度，并输出一整套 Token——而不是把文章里的两套配色写死。

Method distilled from the article 《你的UI廉价，错在颜色》. See `references/principles.md` for the design principles and the desaturation grayscale test.
方法论提炼自文章《你的UI廉价，错在颜色》。设计原则与「去饱和灰度测试」详见 `references/principles.md`。

## Files · 文件结构

- `SKILL.md` — skill manifest (triggers + workflow) · 技能清单（触发场景 + 工作流）
- `scripts/generate_tokens.py` — the token generator · Token 生成引擎
- `references/principles.md` — design principles · 设计原则
- `README.md` — this bilingual document · 本双语说明文档

## License · 许可

MIT
