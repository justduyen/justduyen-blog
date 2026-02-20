---
title: "Định lý Pythagore và ứng dụng"
description: "Tìm hiểu về định lý Pythagore trong tam giác vuông và các ví dụ minh họa."
images: ["images/cover.png"]
date: 2026-02-20
categories: ["Hình học"]
tags: ["hinh-hoc", "toan-co-ban"]
draft: false
math: true
---

Định lý Pythagore (Pythagorean theorem) là một trong những định lý nền tảng và quan trọng nhất trong hình học Euclid.

## Phát biểu định lý

Trong một tam giác vuông, bình phương cạnh huyền bằng tổng bình phương của hai cạnh góc vuông.

Nếu tam giác có các cạnh góc vuông là $a$ và $b$, và cạnh huyền là $c$, thì công thức của định lý được biểu diễn như sau:

$$ a^2 + b^2 = c^2 $$

## Ví dụ

Xét một tam giác vuông có hai cạnh góc vuông lần lượt là 3cm và 4cm. Độ dài cạnh huyền $c$ sẽ được tính như sau:

$$ c^2 = 3^2 + 4^2 = 9 + 16 = 25 $$
$$ c = \sqrt{25} = 5 $$

Vậy, cạnh huyền của tam giác có độ dài là 5cm.

## Chứng minh (sử dụng đại số)

Một cách chứng minh phổ biến là xét một hình vuông lớn có cạnh $(a+b)$. Bên trong nó là 4 tam giác vuông (cạnh $a$, $b$, $c$) và một hình vuông nhỏ có cạnh $c$.

Diện tích hình vuông lớn: $$(a+b)^2 = a^2 + 2ab + b^2$$
Diện tích hình vuông lớn cũng bằng tổng diện tích của 4 tam giác và hình vuông nhỏ bên trong:
$$4 \times \left(\frac{1}{2}ab\right) + c^2 = 2ab + c^2$$

Cho hai biểu thức bằng nhau:
$$ a^2 + 2ab + b^2 = 2ab + c^2 $$
$$ \Rightarrow a^2 + b^2 = c^2 $$

Đây chính là điều phải chứng minh.
