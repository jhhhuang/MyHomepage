---
title: "Gaussian Beam Calculator"
date: 2023-05-08T13:18:44.238Z
summary: A calculator for focusing of Gaussian beam. 
draft: false
featured: false
authors:
  - admin
tags:
  - Tools
categories:
  - Tools
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Gaussian Beam Calculator</title>
  <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
  <style>
    .input-group {
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 10px;
      font-size: 10pt;
    }
    .input-group label {
      margin-right: 10px;
      font-size: 10pt;
      width: 180px;
      text-align: right;
    }
    .input-group input, .input-group select {
      margin-right: 5px;
      font-size: 10pt;
      width: 50px;
    }
    #result {
      margin-top: 20px;
      font-size: 10pt;
    }
  </style>
</head>
<body>
  <div id="input">
    <h2 style="font-size: 15pt;">Input</h2>
    <div class="input-container">
      <div class="input-group">
        <label for="F">Focal length \( F \):</label>
        <input type="number" id="F" step="any" required> <span>mm</span>
      </div>
      <div class="input-group">
        <label for="l">Object distance \( l \):</label>
        <input type="number" id="l" step="any" required> <span>mm</span>
      </div>
      <div class="input-group">
        <label for="w0">Input beam radius \( w_0 \):</label>
        <input type="number" id="w0" step="any" required>
        <select id="w0_unit">
          <option value="mm" selected>mm</option>
          <option value="um">μm</option>
        </select>
      </div>
      <div class="input-group">
        <label for="lambda">Wavelength \( \lambda \):</label>
        <input type="number" id="lambda" step="any" required>
        <select id="lambda_unit">
          <option value="nm" selected>nm</option>
          <option value="um">μm</option>
        </select>
      </div>
    </div>
  </div>
  <div id="result">
    <h2 style="font-size: 15pt;">Result</h2>
    <div class="input-container">
      <div class="input-group">
        <label for="w0_prime">Output beam radius \( w'_0 \):</label>
        <span id="w0_prime"></span>
        <select id="w0_prime_unit">
          <option value="mm" selected>mm</option>
          <option value="um">μm</option>
        </select>
      </div>
      <div class="input-group">
        <label for="l_prime">Image distance \( l' \):</label>
        <span id="l_prime"></span> mm
      </div>
    </div>
  </div>

  <script>
    // 获取元素
    const FInput = document.getElementById('F');
    const lInput = document.getElementById('l');
    const w0Input = document.getElementById('w0');
    const w0Unit = document.getElementById('w0_unit');
    const lambdaInput = document.getElementById('lambda');
    const lambdaUnit = document.getElementById('lambda_unit');
    const w0PrimeSpan = document.getElementById('w0_prime');
    const w0PrimeUnit = document.getElementById('w0_prime_unit');
    const lPrimeSpan = document.getElementById('l_prime');

    // 监听输入和单位变化事件，触发计算
    [FInput, lInput, w0Input, w0Unit, lambdaInput, lambdaUnit, w0PrimeUnit].forEach(el => {
      el.addEventListener('input', calculate);
      el.addEventListener('change', calculate);
    });

    // 单位换算辅助函数
    // 转换输入值到米（m）
    function toMeters(value, unit) {
      if (unit === 'mm') return value / 1000;
      if (unit === 'um') return value / 1e6;
      if (unit === 'nm') return value / 1e9;
      return value; // 默认米
    }
    // 从米转换到指定单位
    function fromMeters(value_m, unit) {
      if (unit === 'mm') return value_m * 1000;
      if (unit === 'um') return value_m * 1e6;
      if (unit === 'nm') return value_m * 1e9;
      return value_m;
    }

    function calculate() {
      // 检查输入是否有效
      if (!FInput.value || !lInput.value || !w0Input.value || !lambdaInput.value) {
        w0PrimeSpan.textContent = '';
        lPrimeSpan.textContent = '';
        return;
      }
      const F_m = toMeters(parseFloat(FInput.value), 'mm'); // F 固定单位 mm -> m
      const l_m = toMeters(parseFloat(lInput.value), 'mm'); // l 固定单位 mm -> m
      const w0_m = toMeters(parseFloat(w0Input.value), w0Unit.value);
      const lambda_m = toMeters(parseFloat(lambdaInput.value), lambdaUnit.value);

      // 计算公式
      const denom = Math.pow(l_m - F_m, 2) + Math.pow(Math.PI * Math.pow(w0_m, 2) / lambda_m, 2);
      const l_prime_m = F_m + ( (l_m - F_m) * F_m * F_m ) / denom;
      const w0_prime_squared = (F_m * F_m * w0_m * w0_m) / denom;
      const w0_prime_m = Math.sqrt(w0_prime_squared);

      // 输出单位转换
      const w0_prime_out = fromMeters(w0_prime_m, w0PrimeUnit.value);
      const l_prime_out = l_prime_m * 1000; // l' 输出单位固定mm

      w0PrimeSpan.textContent = w0_prime_out.toFixed(5);
      lPrimeSpan.textContent = l_prime_out.toFixed(5);
    }
  </script>
</body>
</html>

