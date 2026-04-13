# 前端框架集成

### React 组件

```bash
npx astro add react
```

```astro
---
import ReactCounter from '../components/ReactCounter.jsx';
---
<ReactCounter client:load />
```

### Hydration 指令

```astro
<!-- 页面加载时立即加载 -->
<ReactCounter client:load />

<!-- 浏览器空闲时加载 -->
<ReactCounter client:idle />

<!-- 组件进入视口时加载 -->
<ReactCounter client:visible />

<!-- 匹配媒体查询时加载 -->
<ReactCounter client:media="(max-width: 500px)" />

<!-- 仅在客户端渲染（不生成服务端 HTML） -->
<ReactCounter client:only="react" />

<!-- 交互时加载 -->
<ReactCounter client:media="(prefers-reduced-motion: no-preference)" />
```
