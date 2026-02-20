---
title: "Hướng dẫn hiển thị code đẹp trong PaperMod"
description: "Bài mẫu minh họa các cách hiển thị code, line numbers và highlight line."
images: ["images/cover.png"]
date: 2026-02-20
categories: ["Hugo", "PaperMod"]
tags: ["hugo", "papermod", "code", "syntax-highlight"]
draft: false
ShowToc: true
TocOpen: true
---

Bài này là ví dụ mẫu cho chuyên mục **Học lập trình nhanh A-Z**. Mình tổng hợp các kiểu hiển thị code thường dùng để bạn copy/paste cho các bài sau.

## Inline code

Dùng inline code cho tên hàm như `querySelector` hoặc lệnh `hugo server -D`.

## Code block cơ bản

```
<div class="card">
  <h2>Hello</h2>
</div>
```

## Code block có ngôn ngữ

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8" />
    <title>Demo</title>
  </head>
  <body>
    <p>Xin chào</p>
  </body>
</html>
```

## Code block có line numbers + highlight line

{{< highlight js "linenos=table,hl_lines=3 6-7" >}}
const title = "PaperMod Code";
const items = ["html", "css", "js"];

items.forEach((item) => {
  console.log(item);
});
{{< /highlight >}}

## Code block với shortcode của Hugo

{{< highlight bash "linenos=true" >}}
hugo server -D -F
{{< /highlight >}}

## Code block thụt 4 dấu cách

    SELECT id, title
    FROM posts
    WHERE published = true
    ORDER BY created_at DESC;
