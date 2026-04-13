# 性能优化

### 预获取（Prefetch）

```html
<!-- 全局启用 -->
<head>
  <link rel="prefetch" href="/about" />
</head>
```

```astro
<!-- 链接级别控制 -->
<a href="/about" data-astro-prefetch="true">关于</a>
<a href="/secret" data-astro-prefetch="false">秘密</a>
<a href="/api" data-astro-prefetch="hover">仅 hover 时预加载</a>
```

### 视图过渡动画

```html
<!-- 在布局的 <head> 中启用 -->
<meta name="view-transition" content="same-origin" />
```

```css
/* CSS 定义过渡渡元素 */
.card {
  view-transition-name: card;
}
```

### 客户端脚本

```astro
<!-- 模块化脚本（默认，经过构建） -->
<script>
  import { init } from './utils.js';
  init();
</script>

<!-- 内联脚本（跳过构建，原样输出） -->
<script is:inline>
  console.log('原样输出');
</script>
```

### 图像处理最佳实践

```astro
---
import { Image } from 'astro:assets';
import photo from '../images/photo.jpg';
---

<!-- 使用现代格式和懒加载 -->
<Image
  src={photo}
  alt="照片"
  format="avif"
  quality={75}
  loading="lazy"
  decoding="async"
/>
```
