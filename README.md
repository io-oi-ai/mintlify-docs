# Plain · Docs

Mintlify 站源,部署到 https://docs.inplain.app(或后续 Vercel 自定义域)。

## 本地预览

```bash
cd apps/docs
mint dev
# 打开 http://localhost:3000
```

## 验证

```bash
mint validate         # MDX 语法 + frontmatter
mint broken-links     # 链接完整性
mint a11y             # WCAG 检查
```

## 部署

两种路径任选:

### 1. Mintlify Cloud(推荐,最快)

1. 推这个 repo 到 GitHub
2. mintlify.com 连仓 → 选 root = `apps/docs`
3. 自动 deploy,默认 `<project>.mintlify.app`
4. 自定义域 `docs.inplain.app`:DNS 加 CNAME → `cname.mintlify.com`
5. 主站 `/docs` 路由会读 env `NEXT_PUBLIC_DOCS_URL=https://docs.inplain.app`
   后自动 server-redirect 过去

### 2. Self-host(后续考虑)

Mintlify 支持导出 static build,但还在 beta。现阶段 hosted 方案就够。

## 文件组织

```
apps/docs/
├ docs.json                    Mintlify 配置 + navigation
├ index.mdx                    /
├ quickstart.mdx               /quickstart
├ concepts/                    Plain 的 thesis
├ forms/                       Deck / Doc / Sheet 各 1 篇
├ workflow/                    Inspect / cross-doc / share / present
├ brand/                       Upload + batch generate
├ ai/                          MCP + Cursor + Claude Code
├ cli/                         Install / commands / BYOK
└ api/                         Overview / Auth / Agent / Render / Export
```

## MDX 注意事项

- frontmatter 值有英文双引号时,**不能再嵌一对** — 用 `「」` 中文引号或 `'` 单引号
- icons 用 [Lucide](https://lucide.dev/icons) 或 [Font Awesome](https://fontawesome.com/search) 名字
- `<Card>` `<CardGroup>` `<Steps>` `<AccordionGroup>` `<Tip>` `<Note>` `<CodeGroup>` 都是内置组件
