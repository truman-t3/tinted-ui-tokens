# Tinted UI Tokens

[![Type: WorkBuddy Skill](https://img.shields.io/badge/Type-WorkBuddy%20Skill-blue.svg)](https://www.codebuddy.cn)
[![Input: 1 brand color](https://img.shields.io/badge/input-1%20brand%20color-orange.svg)](#what-it-can-do)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

English | [中文](#中文说明)

A WorkBuddy skill that turns one brand color into a complete, production-ready **brand-tinted design-token system** — so your UI stops looking cheap from flat neutral colors.

No pure neutral colors anywhere (`#FFFFFF`, `#000000`, `#808080`): every background, surface, border, text layer, shadow, semantic color, gradient, and icon picks up a few percent of the brand's temperature.

## Who This Is For

- Designers who want a premium, on-brand UI color system without hand-tuning dozens of gray values.
- Developers who want drop-in CSS variables for light + dark mode from a single hex.
- Teams that want a consistent "tinted neutral" language across products.
- Anyone whose UI currently uses pure `#FFF` / `#000` / `#808080` and reads as "flat".

## What It Can Do

- Generate a full token system from **one brand color** (hex).
- Output `tokens.css` with `:root` + `[data-theme="dark"]` custom properties.
- Output a self-contained `preview.html` with a live light / dark toggle.
- Tint backgrounds, surfaces, borders, text hierarchy, shadows, semantic colors, gradients, and icons.
- Nudge semantic colors (error / warning / success) toward the brand temperature.
- Auto-detect warm / cool / balanced temperature from the brand hue.
- Work for **any** brand color (brand-agnostic generator, not two hard-coded palettes).

## Example Workflows

- "Use `#2563EB` to generate a tinted token system" → get `tokens.css` + `preview.html`.
- Refresh an existing UI: drop `tokens.css` in and replace pure neutrals with the tinted set.
- Compare directions: generate for two brand colors and eyeball the previews.
- Hand-tune: change the blend factor in `build_tokens()` for a stronger or weaker tint.

## Requirements

- Python 3.10+ (the skill uses the managed WorkBuddy Python runtime).
- No external dependencies — `generate_tokens.py` is standard library only.

## Compatibility

| Environment | Requirement | Status |
| --- | --- | --- |
| WorkBuddy | Skill runtime | Supported |
| Python | 3.10+ | Tested |
| OS | Windows / macOS / Linux | Tested on Windows |

## Install

This is a WorkBuddy skill. To install it, clone into your user-level skills directory:

```bash
git clone https://github.com/truman-t3/tinted-ui-tokens ~/.workbuddy/skills/tinted-ui-tokens
```

Or copy the folder `tinted-ui-tokens/` into `~/.workbuddy/skills/`. WorkBuddy picks it up automatically.

## How to Use (in WorkBuddy)

Invoke the skill by asking, for example:

> 用 `#2563EB` 出一套染色 Token 系统

The skill runs `scripts/generate_tokens.py` and presents `preview.html` + `tokens.css`.

## CLI Usage

```bash
python scripts/generate_tokens.py --brand "#2563EB" --name "Acme" --out "./out"
```

- `--brand` (required): any hex color.
- `--name` (optional): label shown in the preview header.
- `--out` (optional): output folder, created if missing.
- `--format css|html|both` (optional, default `both`).

## Output

`tokens.css` defines, for `:root` / `[data-theme="light"]` and `[data-theme="dark"]`:

- `--color-brand`, `--color-brand-subtle`
- `--color-bg`, `--color-surface`, `--color-surface-2`, `--color-border`, `--color-border-strong`
- `--color-text`, `--color-text-2`, `--color-text-muted`
- `--color-error` / `-subtle`, `--color-warning` / `-subtle`, `--color-success` / `-subtle`
- `--shadow-sm`, `--shadow-md`, `--shadow-lg`

No pure `#FFFFFF`, `#000000`, or `#808080` is emitted anywhere.

## How It Works

The generator is **brand-agnostic**: it blends the brand hue into each neutral ramp with a small chroma, derives a warm / cool / balanced temperature, and emits a full token set — instead of hard-coding the two palettes from the original essay.

Method distilled from the article 《你的UI廉价，错在颜色》. See `references/principles.md` for the design principles and the desaturation grayscale test.

## Files

- `SKILL.md` — skill manifest (triggers + workflow)
- `scripts/generate_tokens.py` — the token generator
- `references/principles.md` — design principles
- `README.md` — this document

## Notes

The generated tokens intentionally keep the brand tint subtle (a few percent of chroma) so the UI reads as "designed" rather than "themed". Validate a system with the grayscale test in `references/principles.md`.

## Roadmap

- [ ] Tailwind / Figma variable export
- [ ] Brand-color extraction from an uploaded screenshot
- [ ] More example palettes (cool / warm / balanced) on a comparison page
- [ ] GitHub Action to validate the skill on every change

## License

MIT

---

# 中文说明

[English](#tinted-ui-tokens) | 中文

一个 WorkBuddy 技能：输入一个品牌色，自动生成一套完整、可直接上线的「染色中性色」设计 Token 系统——让你的 UI 不再因为扁平的中性色而显得廉价。

任何地方都不使用纯中性色（`#FFFFFF`、`#000000`、`#808080`）：每一个背景、表面、边框、文字层级、阴影、语义色、渐变与图标，都带上一小撮品牌色的温度。

## 适合谁使用

- 想要高级、统一品牌感配色，又不想手动调几十个灰阶的设计师。
- 想用一个 hex 直接得到可即用的明 / 暗双模式 CSS 变量的开发者。
- 希望跨产品保持一致的「染色中性色」语言规范的团队。
- 当前 UI 还在用纯 `#FFF` / `#000` / `#808080`、整体显得「平」的任何人。

## 能做什么

- 只需**一个品牌色**（hex）就生成一整套 Token 系统。
- 输出 `tokens.css`，含 `:root` 与 `[data-theme="dark"]` 自定义属性。
- 输出一份自包含的 `preview.html`，带明 / 暗实时切换。
- 为背景、表面、边框、文字层级、阴影、语义色、渐变、图标全部染色。
- 把语义色（错误 / 警告 / 成功）轻推至品牌色温。
- 根据品牌色相自动判定暖 / 冷 / 中性三种温度。
- 对任意品牌色都适用（品牌无关的生成器，而非写死的两套配色）。

## 典型使用场景

- 「用 `#2563EB` 出一套染色 Token 系统」→ 得到 `tokens.css` + `preview.html`。
- 翻新现有 UI：把 `tokens.css` 丢进去，用染色集合替换纯中性色。
- 对比方向：分别用两个品牌色各生成一套，直接看预览挑方向。
- 手动微调：改 `build_tokens()` 里的混合系数，让染色更强或更弱。

## 使用要求

- Python 3.10+（技能默认使用 WorkBuddy 托管的 Python 运行时）。
- 无外部依赖——`generate_tokens.py` 仅用标准库。

## 版本兼容表

| 环境 | 要求 | 状态 |
| --- | --- | --- |
| WorkBuddy | 技能运行时 | 支持 |
| Python | 3.10+ | 已测试 |
| 操作系统 | Windows / macOS / Linux | 已在 Windows 测试 |

## 安装

这是一个 WorkBuddy 技能。安装方式：克隆到你的用户级技能目录：

```bash
git clone https://github.com/truman-t3/tinted-ui-tokens ~/.workbuddy/skills/tinted-ui-tokens
```

或者把 `tinted-ui-tokens/` 文件夹复制到 `~/.workbuddy/skills/`。WorkBuddy 会自动识别。

## 使用方法（在 WorkBuddy 中）

像下面这样唤起技能即可：

> 用 `#2563EB` 出一套染色 Token 系统

技能会运行 `scripts/generate_tokens.py`，并展示 `preview.html` 与 `tokens.css`。

## 命令行用法

```bash
python scripts/generate_tokens.py --brand "#2563EB" --name "Acme" --out "./out"
```

- `--brand`（必填）：任意 hex 颜色。
- `--name`（可选）：预览页顶部显示的标签。
- `--out`（可选）：输出目录，不存在则自动创建。
- `--format css|html|both`（可选，默认 `both`）。

## 输出内容

`tokens.css` 为 `:root` / `[data-theme="light"]` 与 `[data-theme="dark"]` 定义：

- `--color-brand`、`--color-brand-subtle`
- `--color-bg`、`--color-surface`、`--color-surface-2`、`--color-border`、`--color-border-strong`
- `--color-text`、`--color-text-2`、`--color-text-muted`
- `--color-error` / `-subtle`、`--color-warning` / `-subtle`、`--color-success` / `-subtle`
- `--shadow-sm`、`--shadow-md`、`--shadow-lg`

任何位置都不会输出纯 `#FFFFFF`、`#000000` 或 `#808080`。

## 工作原理

生成器是**品牌无关**的：它把品牌色相以极小的彩度混入每条中性色阶，推导出暖 / 冷 / 中性三种温度，并输出一整套 Token——而不是把文章里的两套配色写死。

方法论提炼自文章《你的UI廉价，错在颜色》。设计原则与「去饱和灰度测试」详见 `references/principles.md`。

## 文件结构

- `SKILL.md` — 技能清单（触发场景 + 工作流）
- `scripts/generate_tokens.py` — Token 生成引擎
- `references/principles.md` — 设计原则
- `README.md` — 本说明文档

## 说明

生成的 Token 故意把品牌染色保持在很小的比例（几个百分点的彩度），让界面读起来像「精心设计」而非「套了主题色」。可用 `references/principles.md` 里的灰度测试来验证一套系统是否合格。

## 路线图

- [ ] 输出 Tailwind / Figma 变量
- [ ] 从上传的截图自动提取品牌色
- [ ] 在对比页上给出更多示例配色（冷 / 暖 / 中性）
- [ ] 用 GitHub Action 在每次改动时自动校验技能

## 开源协议

MIT
