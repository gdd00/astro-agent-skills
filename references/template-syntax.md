# 模板语法

### 变量与表达式

```astro
---
const name = "Astro";
const items = ["苹果", "香蕉", "橙子"];
const isVisible = true;
---

<!-- 变量输出 -->
<h1>你好 {name}!</h1>

<!-- 条件渲染 -->
{isVisible && <p>显示内容</p>}
{isVisible ? <p>显示</p> : <p>隐藏</p>}

<!-- 列表渲染 -->
<ul>
  {items.map(item => <li>{item}</li>)}
</ul>

<!-- 动态标签（必须大写） -->
---
const Tag = 'div';
---
<Tag>动态 div</Tag>
```

### 片段（Fragment）

```astro
---
import { Fragment } from 'astro';
---
<Fragment>
  <p>第一个</p>
  <p>第二个</p>
</Fragment>

<!-- 简写 -->
<>
  <p>第一个</p>
  <p>第二个</p>
</>
```

### 传递多个子元素到命名插槽

```astro
<CustomTable>
  <Fragment slot="header">
    <tr><th>名称</th><th>数量</th></tr>
  </Fragment>
  <Fragment slot="body">
    <tr><td>商品 A</td><td>10</td></tr>
    <tr><td>商品 B</td><td>20</td></tr>
  </Fragment>
</CustomTable>
```

### Astro.slots 工具函数

```astro
---
// 以编程方式操作插槽内容
const html = await Astro.slots.render('default');
const hasContent = await Astro.slots.has('header');
---
```

### Astro.self 递归组件

```astro
---
const { items, depth = 0 } = Astro.props;
---
<ul>
  {items.map(item => (
    <li>
      {item.name}
      {item.children && <Astro.self items={item.children} depth={depth + 1} />}
    </li>
  ))}
</ul>
```
