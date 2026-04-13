# 项目结构

```
my-project/
├── src/
│   ├── components/     # 可复用的 Astro 组件 (.astro)
│   ├── layouts/        # 页面布局组件
│   ├── pages/          # 基于文件的路由 (.astro, .md, .mdx)
│   │   ├── index.astro
│   │   └── blog/
│   │       ├── index.astro
│   │       └── [slug].astro   # 动态路由
│   ├── content/        # 内容集合 (Markdown/MDX)
│   │   └── blog/
│   │       ├── post-1.md
│   │       └── post-2.md
│   └── env.d.ts        # 全局类型声明
├── public/             # 静态资源（不经过构建）
│   └── favicon.svg
├── astro.config.mjs    # Astro 配置
├── tsconfig.json       # TypeScript 配置
└── package.json
```
