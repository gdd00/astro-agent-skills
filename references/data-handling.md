# 数据处理

### 数据获取

```astro
---
// 在 frontmatter 中使用顶层 await
const response = await fetch('https://api.example.com/data.json');
const data = await response.json();

// 批量导入本地文件
const modules = import.meta.glob('./data/*.json', { eager: true });

// 使用 Astro.glob() 读取 Markdown/MDX
const posts = await Astro.glob('../content/blog/*.md');
---

{data.map(item => <div>{item.name}</div>)}
```

### 环境变量

```bash
# .env
DATABASE_URL="postgresql://localhost:5432/mydb"
API_KEY="secret"
PUBLIC_API_URL="https://api.example.com"
```

```astro
---
// 服务端访问（无前缀）
const dbUrl = import.meta.env.DATABASE_URL;

// 客户端访问（必须 PUBLIC_ 前缀）
const apiUrl = import.meta.env.PUBLIC_API_URL;
---
```

```typescript
// astro.config.mjs - 环境变量验证
import { defineConfig } from 'astro/config';

export default defineConfig({
  experimental: {
    env: {
      schema: {
        DATABASE_URL: envField.string({ context: 'server', access: 'secret' }),
        PORT: envField.number({ context: 'server', access: 'public', default: 4321 }),
        PUBLIC_API_URL: envField.string({ context: 'client', access: 'public' }),
      },
    },
  },
});
```
