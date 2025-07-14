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
    const h = 4.135667516e-15; // eV·s
    const kB = 1.380649e-23; // J/K
    const eV_to_J = 1.602176634e-19;
    const kB_eV = kB / eV_to_J; // eV/K

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
        eV.value = meV.value * 1e-3;
        eVconvert();
      }
    }

    function nmconvert() {
      with (document.conversion) {
        eV.value = h * c / nm.value * 1e9;
        eVconvert();
      }
    }

    function micronconvert() {
      with (document.conversion) {
        eV.value = h * c / micron.value * 1e6;
        eVconvert();
      }
    }

    function wavnumconvert() {
      with (document.conversion) {
        eV.value = wavnum.value * h * c * 100;
        eVconvert();
      }
    }

    function THzconvert() {
      with (document.conversion) {
        eV.value = h * THz.value * 1e12;
        eVconvert();
      }
    }

    function MHzconvert() {
      with (document.conversion) {
        eV.value = h * MHz.value * 1e6;
        eVconvert();
      }
    }

    function fsconvert() {
      with (document.conversion) {
        eV.value = h / fs.value * 1e15;
        eVconvert();
      }
    }

    function psconvert() {
      with (document.conversion) {
        fs.value = ps.value * 1e3;
        fsconvert();
      }
    }

    function Kconvert() {
      with (document.conversion) {
        eV.value = K.value * kB_eV;
        eVconvert();
      }
    }
  </script>
</body>
</html>
