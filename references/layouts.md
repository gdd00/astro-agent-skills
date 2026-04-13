# 布局

布局是接收子内容的特殊组件：

```astro
<!-- src/layouts/BaseLayout.astro -->
---
const { title, description } = Astro.props;
---
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width" />
  <title>{title}</title>
  <meta name="description" content={description} />
  <slot name="head" />
</head>
<body>
  <header>
    <nav><!-- 导航 --></nav>
  </header>
  <main>
    <slot />  <!-- 页面内容 -->
  </main>
  <footer>
    <slot name="footer" />
  </footer>
</body>
</html>
```

```astro
<!-- src/pages/about.astro -->
---
import BaseLayout from '../layouts/BaseLayout.astro';
---
<BaseLayout title="关于" description="关于我们">
  <h1>关于我们的团队</h1>
  <p>这是关于页面内容</p>
</BaseLayout>
```
