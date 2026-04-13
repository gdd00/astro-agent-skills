# 路由与页面

### 文件路由

`src/pages/` 中的文件自动映射为 URL：

| 文件路径 | URL |
|---------|-----|
| `src/pages/index.astro` | `/` |
| `src/pages/about.astro` | `/about` |
| `src/pages/blog/index.astro` | `/blog` |

### 动态路由

```astro
<!-- src/pages/blog/[slug].astro -->
---
import { getCollection } from 'astro:content';

export async function getStaticPaths() {
  const posts = await getCollection('blog');
  return posts.map(post => ({
    params: { slug: post.slug },
    props: { post },
  }));
}

const { post } = Astro.props;
---
<article>
  <h1>{post.data.title}</h1>
  <Content />
</article>
```

### 端点路由

```typescript
// src/pages/api/users.ts
import type { APIRoute } from 'astro';

export const GET: APIRoute = async ({ request, params }) => {
  const users = await db.users.findMany();
  return new Response(JSON.stringify(users), {
    headers: { 'Content-Type': 'application/json' },
  });
};

export const POST: APIRoute = async ({ request }) => {
  const body = await request.json();
  const user = await db.users.create(body);
  return new Response(JSON.stringify(user), { status: 201 });
};
```

### 中间件

```typescript
// src/middleware.ts
import { defineMiddleware } from 'astro:middleware';

export const onRequest = defineMiddleware(async (context, next) => {
  // 请求处理前
  console.log('请求:', context.url.pathname);

  // 调用下一个中间件或路由
  const response = await next();

  // 响应处理后
  response.headers.set('X-Request-ID', crypto.randomUUID());
  return response;
});
```
