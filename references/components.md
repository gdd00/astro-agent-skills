# 组件基础

### 组件结构

Astro 组件由两部分组成：

```astro
---
// 组件脚本（Frontmatter）- 在服务端运行
import Banner from './Banner.astro';
import ReactCounter from './Counter.jsx';

const { title = "默认标题" } = Astro.props;
const posts = await fetch('https://api.example.com/posts').then(r => r.json());
---

<!-- 组件模板 - 生成 HTML 输出 -->
<Banner />
<h1>{title}</h1>
<ul>
  {posts.map(post => <li>{post.title}</li>)}
</ul>
<ReactCounter client:load />
```

### Props（参数）

```astro
---
// 定义 Props 类型（TypeScript 自动推断）
interface Props {
  title: string;
  count?: number;
  items: Array<{ name: string }>;
}

const { title, count = 0, items } = Astro.props;
---
<h1>{title} - {count}</h1>
```

### 插槽（Slots）

**默认插槽：**

```astro
<!-- Wrapper.astro -->
---
const { title } = Astro.props;
---
<div>
  <h1>{title}</h1>
  <slot />  <!-- 子内容注入这里 -->
</div>
```

```astro
<!-- 使用 -->
<Wrapper title="我的页面">
  <p>这里是内容</p>
</Wrapper>
```

**命名插槽：**

```astro
<!-- Card.astro -->
<div>
  <slot name="header" />
  <slot />  <!-- 默认插槽 -->
  <slot name="footer" />
</div>
```

```astro
<Card>
  <img slot="header" src="/banner.jpg" />
  <p>主要内容</p>
  <p slot="footer">版权信息</p>
</Card>
```

**插槽回退：**

```astro
<slot>
  <p>当没有子元素传入时显示此回退内容</p>
</slot>
```

### HTML 组件

`.html` 文件可以作为组件使用，但：
- 不支持 frontmatter 和动态表达式
- `<script>` 标签默认带 `is:inline`
- 只能引用 `public/` 中的资源
