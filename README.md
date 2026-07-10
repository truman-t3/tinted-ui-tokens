# tinted-ui-tokens

A WorkBuddy skill that generates a complete, production-ready **brand-tinted design-token system** from a single brand color — so your UI stops looking cheap because of flat neutral colors.

No pure neutral colors anywhere (`#FFFFFF`, `#000000`, `#808080`): every surface, border, text, shadow, semantic color, gradient, and icon picks up a few percent of the brand's temperature.

## What it does

- **Input:** one brand color (hex) + optional name / style
- **Output:** `tokens.css` (`:root` + `[data-theme="dark"]`) and a self-contained `preview.html`
- **Covers:** backgrounds, surfaces, borders, text hierarchy, shadows, semantic colors (error / warning / success nudged toward the brand's temperature), gradients, icons, and dark mode

## Usage

Invoke the skill inside WorkBuddy. Say something like:

> 用 `#2563EB` 出一套染色 Token 系统

and it runs `scripts/generate_tokens.py` to produce the files.

## How it works

The generator is **brand-agnostic**: it mixes the brand hue into a neutral ramp with a small chroma, derives a warm/cool/balanced temperature, and emits a full token set — instead of hard-coding the two palettes from the article.

Method distilled from the article 《你的UI廉价，错在颜色》. See `references/principles.md` for the design principles and the desaturation grayscale test.

## Files

- `SKILL.md` — skill manifest (triggers + workflow)
- `scripts/generate_tokens.py` — the token generator
- `references/principles.md` — design principles

## License

MIT
