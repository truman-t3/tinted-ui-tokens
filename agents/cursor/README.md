# tinted-ui-tokens-skills on Cursor

Cursor reads rules from `.cursor/rules/` (project) or `~/.cursor/rules/` (global).
A ready-to-use rule file is provided: [`tinted-ui-tokens-skills.mdc`](tinted-ui-tokens-skills.mdc).

## Install · 安装

Copy the rule into your rules directory:

```bash
# project scope
cp tinted-ui-tokens-skills.mdc <your-project>/.cursor/rules/

# or global scope
cp tinted-ui-tokens-skills.mdc ~/.cursor/rules/
```

Also make the engine available — clone the repo or copy `scripts/generate_tokens.py`
so Cursor can run it:

```bash
git clone https://github.com/truman-t3/tinted-ui-tokens-skills ~/.cursor/skills/tinted-ui-tokens-skills
```

## Use · 使用

The rule has `alwaysApply: false`; invoke by mentioning the task, e.g.:

> generate a tinted UI token system from #2563EB

Cursor follows the instruction, runs `scripts/generate_tokens.py`, and returns
`tokens.css` + `preview.html`.
