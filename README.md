# Astro Agent Skills

这是一个专为 agent 设计的 Astro 开发技能包，提供全面的 Astro 框架知识。

## 概述

Astro 是一个现代化的 Web 框架，专注于内容驱动的网站构建。通过群岛架构（Islands Architecture）、服务器优先渲染和零 JavaScript 默认输出，实现卓越的性能和开发体验。

## 技能结构

### SKILL.md
主技能文件，包含：
- **概述**：Astro 核心概念简介
- **快速索引**：各主题对应的参考文档链接
- **常用命令**：开发和构建相关命令
- **关键要点**：重要概念和最佳实践总结

此文件设计为轻量级，加载时消耗极少 token，确保快速响应。

### references/ 目录
详细文档集合，按主题分类存储：
- `core-concepts.md` - 群岛架构、为什么选择 Astro
- `project-structure.md` - 项目目录结构
- `components.md` - 组件系统（Props、Slots）
- `layouts.md` - 布局组件
- `routing.md` - 路由、动态路由、中间件
- `styling.md` - CSS 作用域、Tailwind、Sass
- `content-management.md` - Content Collections、Markdown 处理
- `data-handling.md` - 数据获取、环境变量
- `server-features.md` - SSR、Actions、Sessions
- `framework-integrations.md` - React/Vue 集成、Hydration 指令
- `directives.md` - 组件指令、模板指令
- `template-syntax.md` - 变量、条件渲染、Fragment
- `runtime-apis.md` - astro:content/assets/i18n/middleware
- `configuration.md` - astro.config、tsconfig 配置
- `performance.md` - Prefetch、视图过渡、图像优化

## 使用方式

1. **加载技能**：AI 助手加载 `SKILL.md`，获取快速索引和关键信息
2. **按需查询**：当用户提问特定主题时，读取对应的 `references/*.md` 文件获取详细内容
3. **节省资源**：此设计大幅减少初始加载的 token 消耗，提高响应效率

## 适用场景

- Astro 项目开发咨询
- 框架特性解释
- 最佳实践指导
- 问题排查和调试
- 性能优化建议

## 贡献

如需更新或扩展技能内容，请修改相应 `.md` 文件并保持结构一致。