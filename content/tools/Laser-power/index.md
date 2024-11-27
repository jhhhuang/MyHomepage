---
title: "Laser Power Calculator"
date: 2024-11-27T13:18:44.238Z
summary: Laser beam radius and fluence calculator.
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
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 20px;
        }
        h1 {
            text-align: center;
            margin-bottom: 20px;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            font-weight: bold;
            margin-bottom: 5px;
            display: block;
        }
        input {
            width: 100%;
            padding: 10px;
            font-size: 16px;
            box-sizing: border-box;
        }
        button {
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 16px;
            width: 100%;
        }
        button:hover {
            background-color: #45a049;
        }
        .result {
            margin-top: 20px;
            padding: 10px;
            border: 1px solid #ddd;
            background-color: #f9f9f9;
        }
    </style>
</head>
<body>
    <form id="calculator">
        <div class="form-group">
            <label for="P1">Power before pinhole (\(P_1\), mW):</label>
            <input type="number" id="P1" step="0.01" required>
        </div>
        <div class="form-group">
            <label for="P2">Power after pinhole (\(P_2\), mW):</label>
            <input type="number" id="P2" step="0.01" required>
        </div>
        <div class="form-group">
            <label for="r0">Pinhole radius (\(r_0\), μm):</label>
            <input type="number" id="r0" step="0.01" required>
        </div>
        <div class="form-group">
            <label for="P">Laser power (\(P\), mW):</label>
            <input type="number" id="P" step="0.01" required>
        </div>
        <div class="form-group">
            <label for="frep">Repetition rate (\(f_{\text{rep}}\), Hz):</label>
            <input type="number" id="frep" step="1" required>
        </div>
        <button type="button" onclick="calculate()">Calculate</button>
    </form>
    <div class="result" id="result"></div>

    <script>
        function calculate() {
            // Get input values
            const P1 = parseFloat(document.getElementById('P1').value);
            const P2 = parseFloat(document.getElementById('P2').value);
            const r0 = parseFloat(document.getElementById('r0').value) * 1e-6; // Convert μm to meters
            const P = parseFloat(document.getElementById('P').value) * 1e-3; // Convert mW to W
            const frep = parseFloat(document.getElementById('frep').value);

            // Validate input
            if (isNaN(P1) || isNaN(P2) || isNaN(r0) || isNaN(P) || isNaN(frep)) {
                document.getElementById('result').innerHTML = "Please enter all values correctly.";
                return;
            }
            if (P2 >= P1) {
                document.getElementById('result').innerHTML = "Error: \(P_2\) must be less than \(P_1\).";
                return;
            }

            // Beam radius calculation
            const lnFactor = Math.log(1 / (1 - (P2 / P1)));
            const w = Math.sqrt(2) * r0 / Math.sqrt(lnFactor);

            // Laser fluence calculation in J/m^2
            const fluenceJPerM2 = P / (frep * (Math.PI * Math.pow(w, 2) / 2));
            const fluenceMJPerCM2 = fluenceJPerM2 * 0.1; // Convert to mJ/cm^2

            // Display results
            document.getElementById('result').innerHTML = `
                <div>
                    <p>Beam Radius (\(w\)): <strong>${(w * 1e6).toFixed(2)} μm</strong></p>
                    <p>Laser Fluence: <strong>${fluenceMJPerCM2.toFixed(6)} mJ/cm²</strong></p>
                </div>
            `;
        }
    </script>
</body>
</html>


