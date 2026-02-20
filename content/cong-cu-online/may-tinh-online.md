---
title: "Máy tính online (bài mẫu)"
description: "Bài mẫu để test chuyên mục Công cụ online."
images: ["images/cover.png"]
date: 2026-02-20
draft: false
---

Đây là **máy tính cơ bản chạy trực tiếp** ngay trong bài viết.

{{< rawhtml >}}
<style>
  .calc {
    max-width: 340px;
    margin: 18px auto;
    border: 1px solid #d0d7de;
    border-radius: 16px;
    background: linear-gradient(180deg, #ffffff 0%, #f6f8fa 100%);
    padding: 14px;
    box-shadow: 0 8px 24px rgba(140, 149, 159, 0.12);
  }
  .calc-display {
    font-size: 30px;
    text-align: right;
    padding: 14px 12px;
    border-radius: 10px;
    background: #ffffff;
    border: 1px solid #d0d7de;
    margin-bottom: 12px;
    font-variant-numeric: tabular-nums;
  }
  .calc-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 8px;
  }
  .calc-grid button {
    padding: 12px 0;
    border-radius: 10px;
    border: 1px solid #d0d7de;
    background: #ffffff;
    font-size: 18px;
    cursor: pointer;
    transition: transform 120ms ease, background 120ms ease, border-color 120ms ease;
  }
  .calc-grid button:hover {
    background: #eef2f6;
  }
  .calc-grid button:active {
    transform: translateY(1px);
  }
  .calc-grid .span-2 {
    grid-column: span 2;
  }
  .calc-grid .op {
    background: #0a58ca;
    color: #ffffff;
    border-color: #0a58ca;
  }
  .calc-grid .op:hover {
    background: #0b5ed7;
    border-color: #0b5ed7;
  }
  .calc-grid .eq {
    background: #1f883d;
    color: #ffffff;
    border-color: #1f883d;
  }
  .calc-grid .eq:hover {
    background: #1a7f37;
    border-color: #1a7f37;
  }
  @media (prefers-color-scheme: dark) {
    .calc {
      border-color: #30363d;
      background: linear-gradient(180deg, #161b22 0%, #0d1117 100%);
      box-shadow: 0 8px 24px rgba(0, 0, 0, 0.35);
    }
    .calc-display {
      background: #0d1117;
      border-color: #30363d;
      color: #c9d1d9;
    }
    .calc-grid button {
      background: #161b22;
      border-color: #30363d;
      color: #c9d1d9;
    }
    .calc-grid button:hover {
      background: #1f242b;
    }
  }
</style>

<div class="calc" id="calc-app">
  <div class="calc-display" id="calc-display">0</div>
  <div class="calc-grid">
    <button data-action="clear">C</button>
    <button data-action="sign">±</button>
    <button data-action="percent">%</button>
    <button class="op" data-action="op" data-value="/">÷</button>

    <button data-action="digit" data-value="7">7</button>
    <button data-action="digit" data-value="8">8</button>
    <button data-action="digit" data-value="9">9</button>
    <button class="op" data-action="op" data-value="*">×</button>

    <button data-action="digit" data-value="4">4</button>
    <button data-action="digit" data-value="5">5</button>
    <button data-action="digit" data-value="6">6</button>
    <button class="op" data-action="op" data-value="-">−</button>

    <button data-action="digit" data-value="1">1</button>
    <button data-action="digit" data-value="2">2</button>
    <button data-action="digit" data-value="3">3</button>
    <button class="op" data-action="op" data-value="+">+</button>

    <button class="span-2" data-action="digit" data-value="0">0</button>
    <button data-action="dot">.</button>
    <button class="eq" data-action="eq">=</button>
  </div>
</div>

<script>
  (function () {
    var display = document.getElementById("calc-display");
    var current = "0";
    var prev = null;
    var op = null;
    var resetNext = false;

    function update() {
      display.textContent = current;
    }

    function inputDigit(d) {
      if (resetNext) {
        current = d;
        resetNext = false;
      } else {
        current = current === "0" ? d : current + d;
      }
      update();
    }

    function inputDot() {
      if (resetNext) {
        current = "0.";
        resetNext = false;
        update();
        return;
      }
      if (current.indexOf(".") === -1) {
        current += ".";
        update();
      }
    }

    function clearAll() {
      current = "0";
      prev = null;
      op = null;
      resetNext = false;
      update();
    }

    function toggleSign() {
      if (current === "0") return;
      current = current[0] === "-" ? current.slice(1) : "-" + current;
      update();
    }

    function percent() {
      var value = parseFloat(current);
      if (isNaN(value)) return;
      current = String(value / 100);
      update();
    }

    function compute(a, b, operator) {
      switch (operator) {
        case "+": return a + b;
        case "-": return a - b;
        case "*": return a * b;
        case "/": return b === 0 ? 0 : a / b;
        default: return b;
      }
    }

    function operate(nextOp) {
      var value = parseFloat(current);
      if (prev === null) {
        prev = value;
      } else if (!resetNext) {
        prev = compute(prev, value, op);
      }
      op = nextOp;
      resetNext = true;
      current = String(prev);
      update();
    }

    function equals() {
      if (op === null || prev === null) return;
      var value = parseFloat(current);
      var result = compute(prev, value, op);
      current = String(result);
      prev = null;
      op = null;
      resetNext = true;
      update();
    }

    document.querySelector("#calc-app .calc-grid").addEventListener("click", function (e) {
      var btn = e.target.closest("button");
      if (!btn) return;
      var action = btn.dataset.action;
      var value = btn.dataset.value;

      if (action === "digit") inputDigit(value);
      else if (action === "dot") inputDot();
      else if (action === "clear") clearAll();
      else if (action === "sign") toggleSign();
      else if (action === "percent") percent();
      else if (action === "op") operate(value);
      else if (action === "eq") equals();
    });

    update();
  })();
</script>
{{< /rawhtml >}}
