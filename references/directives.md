# 指令参考

### 组件指令

| 指令 | 说明 |
|------|------|
| `client:load` | 页面加载时立即加载组件 JS |
| `client:idle` | 浏览器空闲后加载 |
| `client:visible` | 组件进入视口时加载 |
| `client:media` | 匹配媒体查询时加载 |
| `client:only` | 仅客户端渲染，跳过 SSR |

### 模板指令

| 指令 | 说明 |
|------|------|
| `set:html` | 设置内部 HTML（防 XSS 注意） |
| `set:text` | 设置纯文本内容 |
| `is:raw` | 跳过模板处理（用于 `<pre>`, `<code>` 等） |
| `is:global` | CSS 样式全局生效 |
| `is:inline` | 跳过构建，原样输出 |
| `transition:name` | 视图过渡命名 |
| `transition:persist` | 视图过渡期间保留组件状态 |
| `define:vars` | 在 `<style>` 或 `<script>` 中使用 JS 变量 |

```astro
<!-- set:html -->
<div set:html={rawHtmlContent} />

<!-- define:vars -->
<script define:vars={{ count }}>
  console.log(count);
</script>

<style define:vars={{ color }}>
  .text { color: var(--color); }
</style>
```
