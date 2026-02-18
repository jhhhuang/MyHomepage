---
title: "Compound Lens Calculator"
date: 2023-05-08T13:18:44.238Z
summary: A calculator for compound lens. 
draft: false
featured: false
authors:
  - admin
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
            align-items: center;
            margin-top: 20px;
            font-size: 10pt;
        }
    </style>
</head>
<body>
  <div class="container">
    <h2 style="font-size: 15pt;">Input</h2>
    <div class="input-group">
      <label for="f1">First lens \(f_1\):</label>
      <input type="number" id="f1" name="f1" oninput="calculateResults()">
    </div>
    <div class="input-group">
      <label for="f2">Second lens \(f_2\):</label>
      <input type="number" id="f2" name="f2" oninput="calculateResults()">
    </div>
    <div class="input-group">
      <label for="d">Distance \(d\):</label>
      <input type="number" id="d" name="d" oninput="calculateResults()">
    </div>
    <h2 style="font-size: 15pt;">Result</h2>
    <div class="input-group">
      <p>Effective focal length \(f\): <span id="f"></span></p>
    </div>
    <div class="input-group">
      <p>FFL: <span id="ffl"></span></p>
    </div>
    <div class="input-group">
      <p>BFL: <span id="bfl"></span></p>
    </div>
  </div>

  <script>
    function calculateResults() {
      const f1 = parseFloat(document.getElementById('f1').value);
      const f2 = parseFloat(document.getElementById('f2').value);
      const d = parseFloat(document.getElementById('d').value);

      const f = (f1 * f2) / (f1 + f2 - d);
      const ffl = (f1 * (f2 - d)) / (f1 + f2 - d);
      const bfl = (f2 * (f1 - d)) / (f1 + f2 - d);

      document.getElementById('f').textContent = f.toFixed(2);
      document.getElementById('ffl').textContent = ffl.toFixed(2);
      document.getElementById('bfl').textContent = bfl.toFixed(2);
    }
  </script>
</body>
</html>
