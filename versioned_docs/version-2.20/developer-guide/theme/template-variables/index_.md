---
title: 首页
description: index.html - /
---

import CategoryVo from "../vo/_CategoryVo.md"
import TagVo from "../vo/_TagVo.md"
import ContributorVo from "../vo/_ContributorVo.md";
import ListedPostVo from "../vo/_ListedPostVo.md"

网站的首页模板，在这个模板中默认设置了最新文章列表的变量，也可以通过调用 [Finder API](../finder-apis.md) 和 [主题设置](../settings.md) 来展示其他数据。

## 路由信息

- 模板路径：`/templates/index.html`
- 访问路径：`/`

## 变量

### posts

#### 变量类型

[#UrlContextListResult\<ListedPostVo\>](#urlcontextlistresultlistedpostvo)

#### 示例

```html title="/templates/index.html"
<div>
  <ul>
    <li th:each="post : ${posts.items}">
      <a
        th:text="${post.spec.title}"
        th:href="${post.status.permalink}"
      ></a>
    </li>
  </ul>
  <div th:if="${posts.hasPrevious() || posts.hasNext()}">
    <a
      th:href="@{${posts.prevUrl}}"
    >
      <span>上一页</span>
    </a>
    <span th:text="${posts.page} +' / '+ ${posts.totalPages}"></span>
    <a
      th:href="@{${posts.nextUrl}}"
    >
      <span>下一页</span>
    </a>
  </div>
</div>
```

### _templateId

#### 变量值

`index`

## 类型定义

### CategoryVo

<CategoryVo />

### TagVo

<TagVo />

### ContributorVo

<ContributorVo />

### ListedPostVo

<ListedPostVo />

- [#CategoryVo](#categoryvo)
- [#TagVo](#tagvo)
- [#ContributorVo](#contributorvo)

### UrlContextListResult\<ListedPostVo\>

```json title="UrlContextListResult<ListedPostVo>"
{
  "page": 0,                                   // 当前页码
  "size": 0,                                   // 每页条数
  "total": 0,                                  // 总条数
  "items": "List<#ListedPostVo>",              // 文章列表数据
  "first": true,                               // 是否为第一页
  "last": true,                                // 是否为最后一页
  "hasNext": true,                             // 是否有下一页
  "hasPrevious": true,                         // 是否有上一页
  "totalPages": 0,                             // 总页数
  "nextUrl": "string",                         // 下一页链接
  "prevUrl": "string"                          // 上一页链接
}
```

- [#ListedPostVo](#listedpostvo)
