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
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gaussian Beam Calculator</title>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
    <style>
        body {
            font-family: "Times New Roman", Times, serif;
            text-align: center;
        }
        .input-group {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 10px;
        }
        .input-group label {
            margin-right: 10px;
        }
        #result {
            margin-top: 20px;
            font-size: 18px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div id="input">
        <h2>Inputs</h2>
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
                <input type="number" id="w0" step="any" required> <span>mm</span>
            </div>
            <div class="input-group">
                <label for="lambda">Wavelength \( \lambda \):</label>
                <input type="number" id="lambda" step="any" required> <span>nm</span>
            </div>
        </div>
    </div>
    <div id="result">
        <h2>Results</h2>
        <div class="input-container">
            <div class="input-group">
                <label for="w0_prime">Output beam radius \( w'_0 \):</label>
                <span id="w0_prime"></span> mm
            </div>
            <div class="input-group">
                <label for="l_prime">Image distance \( l' \):</label>
                <span id="l_prime"></span> mm
            </div>
        </div>
    </div>
    <script>
        // 获取输入框元素
        var FInput = document.getElementById('F');
        var lInput = document.getElementById('l');
        var w0Input = document.getElementById('w0');
        var lambdaInput = document.getElementById('lambda');
        // 获取结果显示区域元素
        var w0PrimeSpan = document.getElementById('w0_prime');
        var lPrimeSpan = document.getElementById('l_prime');
        // 添加输入框的input事件监听器
        [FInput, lInput, w0Input, lambdaInput].forEach(function(input) {
            input.addEventListener('input', function() {
                calculate();
            });
        });
        function calculate() {
            var F = parseFloat(FInput.value) / 1000; // 转换为米
            var l = parseFloat(lInput.value) / 1000; // 转换为米
            var w0 = parseFloat(w0Input.value) / 1000; // 转换为米
            var lambda = parseFloat(lambdaInput.value) / 1e9; // 转换为米
            var l_prime = F + ((l - F) * Math.pow(F, 2)) / ((l - F) ** 2 + ((Math.PI * Math.pow(w0, 2)) / lambda) ** 2);
            var w0_prime_squared = (Math.pow(F, 2) * Math.pow(w0, 2)) / ((l - F) ** 2 + ((Math.PI * Math.pow(w0, 2)) / lambda) ** 2);
            var w0_prime = Math.sqrt(w0_prime_squared) * 1000; // 转换为毫米
            // 更新结果显示
            w0PrimeSpan.textContent = w0_prime.toFixed(5);
            lPrimeSpan.textContent = (l_prime * 1000).toFixed(5);
        }
    </script>
</body>
</html>
