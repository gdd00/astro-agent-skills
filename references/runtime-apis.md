# 运行时 API

### `astro:content`

```typescript
import { getCollection, getEntry, getEntries, render } from 'astro:content';

const posts = await getCollection('blog');
const post = await getEntry('blog', 'my-post');
const posts = await getEntries(['blog/post-1', 'blog/post-2']);
const { Content } = await render(post);
```

### `astro:assets`（图像处理）

```astro
---
import { Image } from 'astro:assets';
import heroImage from '../images/hero.jpg';
---

<Image
  src={heroImage}
  alt="英雄图片"
  width={800}
  height={600}
  format="webp"
  quality={80}
  loading="lazy"
  widths={[300, 600, 900]}
  sizes="(max-width: 600px) 300px, 900px"
/>
```

### `astro:i18n`（国际化）

```typescript
import {
  getRelativeLocaleUrl,
  getAbsoluteLocaleUrl,
  getCurrentLocale,
  useTranslations,
} from 'astro:i18n';

const url = getRelativeLocaleUrl('zh-CN', '/about');
const locale = getCurrentLocale();
```

### `astro:middleware`

```typescript
import { defineMiddleware, sequence } from 'astro:middleware';

const auth = defineMiddleware(async (context, next) => {
  if (!context.cookies.has('session')) {
    return new Response('Unauthorized', { status: 401 });
  }
  return next();
});

export const onRequest = sequence(auth, logging);
```

### `astro:actions`

```typescript
import { Actions } from 'astro:actions';

// 表单提交
<form actions={Actions.greet}>
  <input name="name" />
  <button type="submit">提交</button>
</form>

// 编程调用
const result = await Actions.greet({ name: "Astro" });
```

### `astro:transitions`（视图过渡）

```typescript
import { navigate, onPageTransition } from 'astro:transitions';

navigate('/about');

onPageTransition.onNavigate = ({ from, to }) => {
  console.log(`从 ${from.url} 到 ${to.url}`);
};
```

### `astro:prefetch`（预获取）

```typescript
import { prefetch } from 'astro:prefetch';
prefetch('/about');
```
