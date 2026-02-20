---
title: "Ví dụ về tương tác DOM với JavaScript"
description: "Cách sử dụng JavaScript để thay đổi nội dung và kiểu dáng của một trang web."
images: ["images/cover.png"]
date: 2026-02-23
categories: ["JavaScript"]
tags: ["javascript", "web-development", "dom"]
draft: false
---

DOM (Document Object Model) là một giao diện lập trình cho các tài liệu HTML và XML. Nó biểu diễn trang web để các chương trình có thể thay đổi cấu trúc, kiểu dáng và nội dung của tài liệu.

Dưới đây là một ví dụ đơn giản về cách sử dụng JavaScript để thay đổi nội dung của một phần tử HTML.

## HTML

Trước tiên, chúng ta cần một file HTML với một vài phần tử để tương tác.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>JS DOM Example</title>
    <style>
      .highlight {
        background-color: yellow;
        font-weight: bold;
      }
    </style>
  </head>
  <body>
    <h1 id="main-heading">Chào mừng!</h1>
    <p>Đây là một ví dụ về tương tác DOM.</p>
    <button id="change-text-btn">Đổi chữ</button>
    <button id="change-style-btn">Đổi style</button>

    <script src="app.js"></script>
  </body>
</html>
```

## JavaScript (app.js)

Bây giờ, chúng ta sẽ viết code JavaScript để thay đổi trang HTML trên khi người dùng nhấp vào các nút.

```javascript
// Chờ cho toàn bộ nội dung trang được tải xong
document.addEventListener("DOMContentLoaded", () => {
  const heading = document.getElementById("main-heading");
  const changeTextBtn = document.getElementById("change-text-btn");
  const changeStyleBtn = document.getElementById("change-style-btn");

  changeTextBtn.addEventListener("click", () => {
    heading.textContent = "Đã thay đổi bằng JavaScript!";
  });

  changeStyleBtn.addEventListener("click", () => {
    heading.classList.toggle("highlight");
  });
});
```

Khi bạn mở file HTML trong trình duyệt và nhấp vào các nút, bạn sẽ thấy tiêu đề `<h1>` thay đổi nội dung và kiểu dáng tương ứng.
