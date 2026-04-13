# 服务端功能

### 按需渲染（SSR）

```astro
---
// 页面级别控制渲染方式
// 默认静态预渲染（prerender = true）
// 设为 false 切换到 SSR
export const prerender = false;

const { user } = Astro.locals;
---
```

```typescript
// astro.config.mts - 全局 SSR
import { defineConfig } from 'astro/config';
import node from '@astrojs/node';

export default defineConfig({
  output: 'server',     // 'static' | 'server' | 'hybrid'
  adapter: node(),
});
```

### Actions（类型安全的服务端动作）

```typescript
// src/actions/index.ts
import { defineAction, z } from 'astro:actions';

export const server = {
  // JSON 输入
  greet: defineAction({
    input: z.object({
      name: z.string().min(1),
    }),
    handler: async ({ name }) => {
      return `Hello, ${name}!`;
    },
  }),

  // 表单数据（支持文件上传）
  upload: defineAction({
    accept: 'form',
    input: z.object({
      file: z.instanceof(File),
      caption: z.string().optional(),
    }),
    handler: async (input) => {
      // 处理上传的文件
      return { success: true };
    },
  }),
};
```

```astro
<!-- 使用 Actions -->
---
import { Actions } from 'astro:actions';
---
<form actions={Actions.greet}>
  <input name="name" />
  <button type="submit">问候</button>
</form>
```

### Sessions（会话管理）

```typescript
// astro.config.mts
import { defineConfig } from 'astro/config';

export default defineConfig({
  output: 'server',
  session: {
    driver: 'database',
    driverConfig: {
      database: {
        url: process.env.DATABASE_URL,
        tableName: 'sessions',
      },
    },
  },
});
```

```astro
---
const session = Astro.session;
await session.set('userId', user.id);
const userId = await session.get('userId');
await session.destroy();
---
```

### 服务器群岛（Server Islands）

```astro
---
// components/SlowComponent.astro
// 这个组件渲染很慢
const data = await fetchSlowData();
---
<server-island name="SlowComponent" id={data.id}>
  <p>加载中...</p>  <!-- 加载回退内容 -->
</server-island>
```
