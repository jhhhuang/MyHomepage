---
title: "Laser Power Calculator"
date: 2023-05-08T13:18:44.238Z
summary: A calculator for laser beam radius and fluence.
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
    <title>Laser Beam Calculator</title>
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
                <label for="P1">Power before pinhole (\(P_1\)):</label>
                <input type="number" id="P1" step="any" required> <span>mW</span>
            </div>
            <div class="input-group">
                <label for="P2">Power after pinhole (\(P_2\)):</label>
                <input type="number" id="P2" step="any" required> <span>mW</span>
            </div>
            <div class="input-group">
                <label for="r0">Pinhole radius (\(r_0\)):</label>
                <input type="number" id="r0" step="any" required> <span>μm</span>
            </div>
            <div class="input-group">
                <label for="P">Laser power (\(P\)):</label>
                <input type="number" id="P" step="any"> <span>mW</span>
            </div>
            <div class="input-group">
                <label for="frep">Repetition rate (\(f_{\text{rep}}\)):</label>
                <input type="number" id="frep" step="any"> <span>Hz</span>
            </div>
        </div>
    </div>
    <div id="result">
        <h2 style="font-size: 15pt;">Result</h2>
        <div class="input-container">
            <div class="input-group">
                <label for="w">Beam Radius (\(w\)):</label>
                <span id="w"></span> μm
            </div>
            <div class="input-group">
                <label for="pulseEnergy">Pulse Energy (\(E\)):</label>
                <span id="pulseEnergy"></span> mJ
            </div>
            <div class="input-group">
                <label for="fluence">Laser Fluence:</label>
                <span id="fluence"></span> mJ/cm²
            </div>
        </div>
    </div>
    <script>
        // 获取输入框元素
        var P1Input = document.getElementById('P1');
        var P2Input = document.getElementById('P2');
        var r0Input = document.getElementById('r0');
        var PInput = document.getElementById('P');
        var frepInput = document.getElementById('frep');
        // 获取结果显示区域元素
        var wSpan = document.getElementById('w');
        var pulseEnergySpan = document.getElementById('pulseEnergy');
        var fluenceSpan = document.getElementById('fluence');
        // 添加输入框的input事件监听器
        [P1Input, P2Input, r0Input, PInput, frepInput].forEach(function(input) {
            input.addEventListener('input', function() {
                calculate();
            });
        });
        function calculate() {
            var P1 = parseFloat(P1Input.value);
            var P2 = parseFloat(P2Input.value);
            var r0 = parseFloat(r0Input.value) * 1e-6; // μm -> 米
            var P = parseFloat(PInput.value) * 1e-3; // mW -> W
            var frep = parseFloat(frepInput.value);
            // 计算光束半径 (w)
            if (!isNaN(P1) && !isNaN(P2) && !isNaN(r0) && P2 < P1) {
                var lnFactor = Math.log(1 / (1 - P2 / P1));
                var w = Math.sqrt(2) * r0 / Math.sqrt(lnFactor);
                wSpan.textContent = (w * 1e6).toFixed(5); // 转换为 μm
            } else {
                wSpan.textContent = "N/A ";
            }
            // 计算单脉冲能量 (E)
            if (!isNaN(P) && !isNaN(frep) && frep > 0) {
                var pulseEnergy = P / frep; // 单脉冲能量公式 E = P / frep
                pulseEnergySpan.textContent = (pulseEnergy * 1e3).toFixed(5); // 转换为 mJ
            } else {
                pulseEnergySpan.textContent = "N/A ";
            }
            // 计算激光能量密度 (Laser Fluence)
            if (!isNaN(P) && !isNaN(frep) && frep > 0 && !isNaN(w)) {
                var fluenceJPerM2 = P / (frep * (Math.PI * Math.pow(w, 2) / 2));
                var fluenceMJPerCM2 = fluenceJPerM2 * 0.1; // 转换为 mJ/cm²
                fluenceSpan.textContent = fluenceMJPerCM2.toFixed(6);
            } else {
                fluenceSpan.textContent = "N/A ";
            }
        }
    </script>
</body>
</html>
