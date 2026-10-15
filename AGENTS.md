# AGENTS.md

## What this repo is

Static HTML/CSS coursework for a web-design class ("高级网页设计"). Flat directory of standalone pages plus `img/`.

- **No build, test, lint, package manager, or CI.** Do not add tooling unless asked.
- **Entry point:** `index.html` — styled hub; currently only 2 cards, both linking deleted files (see Known issues). Open files directly via `file://`; no dev server needed.
- Each page is self-contained: styling lives in an inline `<style>` block. Exception: `5-1.html` links the shared `css.css`.

## 项目规则（必须遵守）

- 所有 CSS 类名、id 名、JS 变量必须以 `Ge_` 开头（如 `.Ge_card`、`#Ge_box`、`Ge_count`）。存量旧页面多为无前缀类名，未经要求不要批量重命名。
- 每条提示词须在执行前**追加**写入 `Ge_prompt.md`（append，不覆盖已有内容），每条包含：时间 `yyyy-mm-dd-hh-mm`、使用的模型、提示词内容。
- 新建的 HTML 文件必须包含指向首页的超链接 `<a href="index.html">`（通常放页首"返回首页"与页脚）。

## Conventions

- All files are UTF-8 with `<meta charset="UTF-8">`. Preserve UTF-8 (no BOM) when editing — PowerShell/shell defaults may write UTF-16 or GBK.
- Filenames contain **spaces** (`3-1 form.html`, `4-1 css2.html`) and **Chinese characters** (`css3选择器.html`). Do not rename or "clean up" names; hrefs must match them exactly.
- Keep edits in the same style: Chinese UI copy, plain vanilla HTML/CSS, no CDN dependencies.

## Known issues (verified 2026-10-12)

- `index.html` cards link `css-units.html` and `css-3d.html` — both files were deleted; links are broken.
- `1.1.html` links `./imag/1.jpg` etc. — the folder is `img/` and the files are `1.png` / `2.png` / `3.png`.
- Hub links only those 2 pages; all other pages (including `11-1.html`) are unlinked from `index.html`.
