# 配置

### astro.config.mts

```typescript
import { defineConfig } from 'astro/config';
import react from '@astrojs/react';
import tailwind from '@astrojs/tailwind';
import sitemap from '@astrojs/sitemap';
import node from '@astrojs/node';

export default defineConfig({
  // 输出模式
  output: 'static',          // 'static' | 'server' | 'hybrid'
  adapter: node(),           // SSR 适配器

  // URL 配置
  site: 'https://example.com',
  base: '/my-app',           // 部署子路径
  trailingSlash: 'ignore',   // 'always' | 'never' | 'ignore'

  // 构建配置
  build: {
    format: 'directory',     // 'file' | 'directory'
    assets: '_astro',        // 静态资源目录名
  },

  // 开发服务器
  server: {
    port: 3000,
    host: true,
  },

  // 集成
  integrations: [react(), tailwind(), sitemap()],

  // Markdown 配置
  markdown: {
    shikiConfig: {
      theme: 'dracula',
      wrap: true,
    },
  },

  // 预获取
  prefetch: {
    prefetchAll: true,
    defaultStrategy: 'hover',
  },

  // 国际化
  i18n: {
    defaultLocale: 'zh-CN',
    locales: ['zh-CN', 'en'],
  },

  // 传递 Vite 配置
  vite: {
    // ...
  },
});
```

### TypeScript 配置

```json
{
  "extends": "astro/tsconfigs/strict",
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@components/*": ["src/components/*"],
      "@layouts/*": ["src/layouts/*"]
    }
  }
}
```

tsconfig 预设选项：
- `astro/tsconfigs/strict` — 推荐，严格模式
- `astro/tsconfigs/strictest` — 最严格
- `astro/tsconfigs/base` — 最小配置
