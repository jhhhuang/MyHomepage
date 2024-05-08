---
title: "Gaussian Beam Calculators"
date: 2022-11-27T13:18:44.238Z
summary: 
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
    <style>
        body {
            font-family: "Times New Roman", Times, serif;
            text-align: center;
        }
        form {
            text-align: left;
            display: inline-block;
        }
        #result {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <h1>Gaussian Beam Calculator</h1>
    <form id="inputForm">
        <label for="F">F:</label>
        <input type="number" id="F" step="any" required> mm<br><br>
        <label for="l">l:</label>
        <input type="number" id="l" step="any" required> mm<br><br>
        <label for="w0">w<sub>0</sub>:</label>
        <input type="number" id="w0" step="any" required> mm<br><br>
        <label for="lambda">λ:</label>
        <input type="number" id="lambda" step="any" required> nm<br><br>
    </form>
    <div id="result"></div>
    <script>
        // 获取输入框元素
        var FInput = document.getElementById('F');
        var lInput = document.getElementById('l');
        var w0Input = document.getElementById('w0');
        var lambdaInput = document.getElementById('lambda');
        // 获取结果显示区域元素
        var resultDiv = document.getElementById('result');
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
            // 显示结果
            resultDiv.innerHTML = "<p>w'<sub>0</sub>:" + w0_prime.toFixed(5) + " mm</p>" + "<p>l':" + (l_prime * 1000).toFixed(5) + " mm</p>";
        }
    </script>
</body>
</html>
