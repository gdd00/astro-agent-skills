# 样式与 CSS

### 组件内样式（默认作用域）

```astro
---
// Astro 组件的 <style> 默认作用域到此组件
---
<h1 class="title">标题</h1>
<style>
  .title {
    color: #333;
    font-size: 2rem;
  }
</style>
```

### 全局样式

```astro
<style is:global>
  /* 全局生效 */
  body { margin: 0; }
</style>
```

### CSS Modules

```astro
---
import styles from './Button.module.css';
---
<button class={styles.primary}>按钮</button>
```

### Tailwind CSS

```bash
npx astro add tailwind
```

```astro
---
// 直接写 Tailwind 类
---
<div class="flex items-center justify-center p-4 bg-gray-100">
  <h1 class="text-3xl font-bold">标题</h1>
</div>
```

### Sass/Less

```bash
npx astro add sass
```

```astro
<style lang="scss">
  $primary: #007bff;
  .button {
    background: $primary;
  }
</style>
```
