---
name: astro-agent-skills
description: Astro 框架开发指南
---

# Astro 开发 Skills 指南

Astro 是以内容驱动的网站最优的 Web 框架，核心特点：群岛架构（Islands）、服务器优先、默认无 JS、UI 框架无关。

> 各主题详细文档见 `references/` 目录，按需读取。

## 快速索引

| 主题 | 参考文件 |
|------|---------|
| 群岛架构、为什么选 Astro | [references/core-concepts.md](references/core-concepts.md) |
| 目录结构 | [references/project-structure.md](references/project-structure.md) |
| 组件（Props、Slots） | [references/components.md](references/components.md) |
| 布局 | [references/layouts.md](references/layouts.md) |
| 路由、动态路由、中间件 | [references/routing.md](references/routing.md) |
| CSS 作用域、Tailwind、Sass | [references/styling.md](references/styling.md) |
| Content Collections、Markdown | [references/content-management.md](references/content-management.md) |
| 数据获取、环境变量 | [references/data-handling.md](references/data-handling.md) |
| SSR、Actions、Sessions | [references/server-features.md](references/server-features.md) |
| React/Vue 集成、Hydration 指令 | [references/framework-integrations.md](references/framework-integrations.md) |
| 组件指令、模板指令 | [references/directives.md](references/directives.md) |
| 变量、条件渲染、Fragment | [references/template-syntax.md](references/template-syntax.md) |
| astro:content/assets/i18n/middleware | [references/runtime-apis.md](references/runtime-apis.md) |
| astro.config、tsconfig | [references/configuration.md](references/configuration.md) |
| Prefetch、视图过渡、图像优化 | [references/performance.md](references/performance.md) |

## 常用命令

```bash
npm create astro@latest     # 创建项目
npm run dev                 # 开发服务器
npm run build               # 构建
npm run preview             # 预览构建结果
npx astro add react         # 添加集成
npx astro check             # 类型检查
```

## 关键要点

1. `.astro` = frontmatter（服务端 JS）+ 模板（HTML），JS 不会泄露到客户端
2. `src/pages/` 目录结构 = URL 路径，`[param]` = 动态参数
3. `client:*` 指令控制 UI 框架组件 hydration 时机
4. Markdown 放 `src/content/`，用 `getCollection()` 类型安全查询
5. `<style>` 默认作用域，支持 CSS Modules、Tailwind、Sass
6. `src/pages/api/` 导出 HTTP 方法处理器
7. 默认零 JS，prefetch + 视图过渡提升导航体验
8. `output: 'static'` 静态部署，`output: 'server'` 需 SSR 适配器
