# 内容管理

### Markdown 页面

```markdown
<!-- src/content/blog/my-post.md -->
---
title: "我的文章"
description: "文章描述"
date: 2024-01-15
tags: ["astro", "webdev"]
author: "作者名"
image: /images/cover.jpg
---

文章内容使用 Markdown 编写...
```

### 内容集合

```typescript
// src/content/config.ts
import { defineCollection, z } from 'astro:content';

const blog = defineCollection({
  type: 'content',
  schema: z.object({
    title: z.string(),
    description: z.string(),
    date: z.date(),
    tags: z.array(z.string()),
    draft: z.boolean().default(false),
    author: z.string().default('Anonymous'),
    image: z.string().optional(),
  }),
});

export const collections = { blog };
```

### 查询内容

```astro
---
import { getCollection, getEntry } from 'astro:content';

// 获取所有文章
const posts = await getCollection('blog');

// 过滤
const published = await getCollection('blog', ({ data }) => !data.draft);

// 获取单个条目
const post = await getEntry('blog', 'my-post-slug');

// 渲染
const { Content } = await post.render();
---

<Content />
```

### 引用关系

```typescript
import { defineCollection, z, reference } from 'astro:content';

const authors = defineCollection({
  type: 'content',
  schema: z.object({
    name: z.string(),
    bio: z.string(),
  }),
});

const blog = defineCollection({
  type: 'content',
  schema: z.object({
    title: z.string(),
    author: reference('authors'),  // 引用作者集合
  }),
});

export const collections = { blog, authors };
```
