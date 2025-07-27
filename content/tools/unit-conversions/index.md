---
title: "Unit Conversions"
date: 2023-05-08T13:18:44.238Z
summary: Unit conversions for spectroscopy.
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
<!-- test -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Unit Conversions</title>
</head>
<body>
  <form name="conversion">
    <table cellpadding="10" align="center" style="border:1px solid #CCC">
      <tbody>
        <tr>
          <td><span style="font-size:10pt">eV: <input name="eV" onkeyup="eVconvert()" value="1" size="15"></span></td>
          <td><span style="font-size:10pt">nm: <input name="nm" onkeyup="nmconvert()" value="1240" size="15"></span></td>
          <td><span style="font-size:10pt">cm<sup>-1</sup>: <input name="wavnum" onkeyup="wavnumconvert()" value="8065.6" size="15"></span></td>
          <td><span style="font-size:10pt">fs: <input name="fs" onkeyup="fsconvert()" value="4.136" size="15"></span></td>
          <td><span style="font-size:10pt">MHz: <input name="MHz" onkeyup="MHzconvert()" value="241800000" size="15"></span></td>
        </tr>
        <tr>
          <td><span style="font-size:10pt">meV: <input name="meV" onkeyup="meVconvert()" value="1000" size="15"></span></td>
          <td><span style="font-size:10pt">µm: <input name="micron" onkeyup="micronconvert()" value="1.24" size="15"></span></td>
          <td><span style="font-size:10pt">THz: <input name="THz" onkeyup="THzconvert()" value="241.8" size="15"></span></td>
          <td><span style="font-size:10pt">ps: <input name="ps" onkeyup="psconvert()" value="0.004" size="15"></span></td>
          <td><span style="font-size:10pt">K: <input name="K" onkeyup="Kconvert()" value="11604.5" size="15"></span></td>
        </tr>
      </tbody>
    </table>
  </form>

  <script>
    const c = 299792458;
    const h = 4.135667516e-15;
    const kB = 1.380649e-23;
    const eV_to_J = 1.602176634e-19;
    const kB_eV = kB / eV_to_J;

    function round_sig(x, sig = 7) {
      return Number.parseFloat(x).toPrecision(sig);
    }

    function eVconvert() {
      with (document.conversion) {
        meV.value = round_sig(eV.value * 1e3);
        nm.value = round_sig(h * c / eV.value * 1e9);
        micron.value = round_sig(h * c / eV.value * 1e6);
        wavnum.value = round_sig(eV.value / (h * c * 100));
        THz.value = round_sig(eV.value / h * 1e-12);
        fs.value = round_sig(h / eV.value * 1e15);
        ps.value = round_sig(h / eV.value * 1e12);
        K.value = round_sig(eV.value / kB_eV);
        MHz.value = round_sig(eV.value / h * 1e-6);
      }
    }

    function meVconvert() {
      with (document.conversion) {
        const eV_val = meV.value * 1e-3;
        eV.value = round_sig(eV_val);
        nm.value = round_sig(h * c / eV_val * 1e9);
        micron.value = round_sig(h * c / eV_val * 1e6);
        wavnum.value = round_sig(eV_val / (h * c * 100));
        THz.value = round_sig(eV_val / h * 1e-12);
        fs.value = round_sig(h / eV_val * 1e15);
        ps.value = round_sig(h / eV_val * 1e12);
        K.value = round_sig(eV_val / kB_eV);
        MHz.value = round_sig(eV_val / h * 1e-6);
      }
    }

    function nmconvert() {
      with (document.conversion) {
        const eV_val = h * c / nm.value * 1e9;
        eV.value = round_sig(eV_val);
        meV.value = round_sig(eV_val * 1e3);
        micron.value = round_sig(nm.value * 1e-3);
        wavnum.value = round_sig(eV_val / (h * c * 100));
        THz.value = round_sig(eV_val / h * 1e-12);
        fs.value = round_sig(h / eV_val * 1e15);
        ps.value = round_sig(h / eV_val * 1e12);
        K.value = round_sig(eV_val / kB_eV);
        MHz.value = round_sig(eV_val / h * 1e-6);
      }
    }

    function micronconvert() {
      with (document.conversion) {
        const eV_val = h * c / micron.value * 1e6;
        eV.value = round_sig(eV_val);
        meV.value = round_sig(eV_val * 1e3);
        nm.value = round_sig(micron.value * 1e3);
        wavnum.value = round_sig(eV_val / (h * c * 100));
        THz.value = round_sig(eV_val / h * 1e-12);
        fs.value = round_sig(h / eV_val * 1e15);
        ps.value = round_sig(h / eV_val * 1e12);
        K.value = round_sig(eV_val / kB_eV);
        MHz.value = round_sig(eV_val / h * 1e-6);
      }
    }

    function wavnumconvert() {
      with (document.conversion) {
        const eV_val = wavnum.value * h * c * 100;
        eV.value = round_sig(eV_val);
        meV.value = round_sig(eV_val * 1e3);
        nm.value = round_sig(h * c / eV_val * 1e9);
        micron.value = round_sig(h * c / eV_val * 1e6);
        THz.value = round_sig(eV_val / h * 1e-12);
        fs.value = round_sig(h / eV_val * 1e15);
        ps.value = round_sig(h / eV_val * 1e12);
        K.value = round_sig(eV_val / kB_eV);
        MHz.value = round_sig(eV_val / h * 1e-6);
      }
    }

    function THzconvert() {
      with (document.conversion) {
        const eV_val = h * THz.value * 1e12;
        eV.value = round_sig(eV_val);
        meV.value = round_sig(eV_val * 1e3);
        nm.value = round_sig(h * c / eV_val * 1e9);
        micron.value = round_sig(h * c / eV_val * 1e6);
        wavnum.value = round_sig(eV_val / (h * c * 100));
        fs.value = round_sig(h / eV_val * 1e15);
        ps.value = round_sig(h / eV_val * 1e12);
        K.value = round_sig(eV_val / kB_eV);
        MHz.value = round_sig(eV_val / h * 1e-6);
      }
    }

    function MHzconvert() {
      with (document.conversion) {
        const eV_val = h * MHz.value * 1e6;
        eV.value = round_sig(eV_val);
        meV.value = round_sig(eV_val * 1e3);
        nm.value = round_sig(h * c / eV_val * 1e9);
        micron.value = round_sig(h * c / eV_val * 1e6);
        wavnum.value = round_sig(eV_val / (h * c * 100));
        THz.value = round_sig(MHz.value / 1e6);
        fs.value = round_sig(h / eV_val * 1e15);
        ps.value = round_sig(h / eV_val * 1e12);
        K.value = round_sig(eV_val / kB_eV);
      }
    }

    function fsconvert() {
      with (document.conversion) {
        const eV_val = h / fs.value * 1e15;
        eV.value = round_sig(eV_val);
        meV.value = round_sig(eV_val * 1e3);
        nm.value = round_sig(h * c / eV_val * 1e9);
        micron.value = round_sig(h * c / eV_val * 1e6);
        wavnum.value = round_sig(eV_val / (h * c * 100));
        THz.value = round_sig(eV_val / h * 1e-12);
        ps.value = round_sig(fs.value / 1e3);
        K.value = round_sig(eV_val / kB_eV);
        MHz.value = round_sig(eV_val / h * 1e-6);
      }
    }

    function psconvert() {
      with (document.conversion) {
        eV.value = roundfive(h / ps.value * 1e12);
        meV.value = roundfive(h / ps.value * 1e15);
        nm.value = roundfive(c * ps.value * 1e-3);
        micron.value = roundfive(c * ps.value * 1e-6);
        wavnum.value = roundfive(1 / (ps.value * c * 100) * 1e12);
        THz.value = roundfive(1 / ps.value);
        fs.value = roundfive(ps.value * 1e3);
        MHz.value = roundfive(eV.value / h * 1e-6);
        K.value = roundfive(eV.value / kB_eV);
      }
    }

    function Kconvert() {
      with (document.conversion) {
        const eV_val = K.value * kB_eV;
        eV.value = round_sig(eV_val);
        meV.value = round_sig(eV_val * 1e3);
        nm.value = round_sig(h * c / eV_val * 1e9);
        micron.value = round_sig(h * c / eV_val * 1e6);
        wavnum.value = round_sig(eV_val / (h * c * 100));
        THz.value = round_sig(eV_val / h * 1e-12);
        fs.value = round_sig(h / eV_val * 1e15);
        ps.value = round_sig(h / eV_val * 1e12);
        MHz.value = round_sig(eV_val / h * 1e-6);
      }
    }
  </script>
</body>
</html>

