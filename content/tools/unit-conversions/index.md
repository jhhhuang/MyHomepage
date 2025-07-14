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
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Unit Conversions</title>
</head>
<body>
  <form name="conversion">
    <table cellpadding="10" align="center" style="border-width:1px" bordercolor="#CCCCCC">
      <tbody>
        <tr>
          <td><span style="font-size:10pt">eV: <input name="eV" onkeyup="eVconvert()" value="1" size="15"></span></td>
          <td><span style="font-size:10pt">nm: <input name="nm" onkeyup="nmconvert()" value="1240" size="15"></span></td>
          <td><span style="font-size:10pt">cm<sup>-1</sup>: <input name="wavnum" onkeyup="wavnumconvert()" value="8065.6" size="15"></span></td>
          <td><span style="font-size:10pt">fs: <input name="fs" onkeyup="fsconvert()" value="4.136" size="15"></span></td>
          <td><span style="font-size:10pt">MHz: <input name="MHz" onkeyup="MHzconvert()" value="24179893" size="15"></span></td>
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
    const kB_eV = 8.617333262e-5;

    function roundfive(num) {
      return (Math.round(num * 10000000) / 10000000).toFixed(7);
    }

    function eVconvert() {
      with (document.conversion) {
        meV.value = roundfive(eV.value * 1e3);
        nm.value = roundfive(h * c / eV.value * 1e9);
        micron.value = roundfive(h * c / eV.value * 1e6);
        wavnum.value = roundfive(eV.value / (h * c * 100));
        THz.value = roundfive(eV.value / h * 1e-12);
        fs.value = roundfive(h / eV.value * 1e15);
        ps.value = roundfive(h / eV.value * 1e12);
        MHz.value = roundfive(eV.value / h * 1e-6);
        K.value = roundfive(eV.value / kB_eV);
      }
    }

    function meVconvert() {
      with (document.conversion) {
        eV.value = roundfive(meV.value * 1e-3);
        nm.value = roundfive(h * c / meV.value * 1e9 * 1e3);
        micron.value = roundfive(h * c / meV.value * 1e6 * 1e3);
        wavnum.value = roundfive(meV.value / (h * c * 100) * 1e-3);
        THz.value = roundfive(meV.value / h * 1e-12 * 1e-3);
        fs.value = roundfive(h / meV.value * 1e15 * 1e3);
        ps.value = roundfive(h / meV.value * 1e12 * 1e3);
        MHz.value = roundfive(meV.value / h * 1e-6 * 1e-3);
        K.value = roundfive(meV.value * 1e-3 / kB_eV);
      }
    }

    function nmconvert() {
      with (document.conversion) {
        eV.value = roundfive(h * c / nm.value * 1e9);
        meV.value = roundfive(h * c / nm.value * 1e12);
        micron.value = roundfive(nm.value * 1e-3);
        wavnum.value = roundfive(1 / (nm.value * 1e-7));
        THz.value = roundfive(c / nm.value * 1e-3);
        fs.value = roundfive(nm.value / c * 1e6);
        ps.value = roundfive(nm.value / c * 1e3);
        MHz.value = roundfive(eV.value / h * 1e-6);
        K.value = roundfive(eV.value / kB_eV);
      }
    }

    function micronconvert() {
      with (document.conversion) {
        eV.value = roundfive(h * c / micron.value * 1e6);
        meV.value = roundfive(h * c / micron.value * 1e9);
        nm.value = roundfive(micron.value * 1e3);
        wavnum.value = roundfive(1 / (micron.value * 1e-4));
        THz.value = roundfive(c / micron.value * 1e-6);
        fs.value = roundfive(micron.value / c * 1e9);
        ps.value = roundfive(micron.value / c * 1e6);
        MHz.value = roundfive(eV.value / h * 1e-6);
        K.value = roundfive(eV.value / kB_eV);
      }
    }

    function wavnumconvert() {
      with (document.conversion) {
        eV.value = roundfive(wavnum.value * h * c * 100);
        meV.value = roundfive(wavnum.value * h * c * 100 * 1e3);
        nm.value = roundfive(1e9 / (wavnum.value * 100));
        micron.value = roundfive(1e6 / (wavnum.value * 100));
        THz.value = roundfive(wavnum.value * c * 100 * 1e-12);
        fs.value = roundfive(1 / (wavnum.value * c * 100) * 1e15);
        ps.value = roundfive(1 / (wavnum.value * c * 100) * 1e12);
        MHz.value = roundfive(eV.value / h * 1e-6);
        K.value = roundfive(eV.value / kB_eV);
      }
    }

    function THzconvert() {
      with (document.conversion) {
        eV.value = roundfive(h * THz.value * 1e12);
        meV.value = roundfive(h * THz.value * 1e15);
        nm.value = roundfive(c / THz.value * 1e-3);
        micron.value = roundfive(c / THz.value * 1e-6);
        wavnum.value = roundfive(THz.value * 1e12 / (c * 100));
        fs.value = roundfive(1 / (THz.value * 1e12) * 1e15);
        ps.value = roundfive(1 / (THz.value * 1e12) * 1e12);
        MHz.value = roundfive(THz.value * 1e6);
        K.value = roundfive(eV.value / kB_eV);
      }
    }

    function fsconvert() {
      with (document.conversion) {
        eV.value = roundfive(h / fs.value * 1e15);
        meV.value = roundfive(h / fs.value * 1e18);
        nm.value = roundfive(c * fs.value * 1e-6);
        micron.value = roundfive(c * fs.value * 1e-9);
        wavnum.value = roundfive(1 / (fs.value * c * 100) * 1e15);
        THz.value = roundfive(1 / fs.value);
        ps.value = roundfive(fs.value * 1e-3);
        MHz.value = roundfive(eV.value / h * 1e-6);
        K.value = roundfive(eV.value / kB_eV);
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

    function MHzconvert() {
      with (document.conversion) {
        THz.value = roundfive(MHz.value * 1e-6);
        eV.value = roundfive(h * MHz.value * 1e6);
        meV.value = roundfive(h * MHz.value * 1e9);
        wavnum.value = roundfive((h * MHz.value * 1e6) / (h * c * 100));
        nm.value = roundfive(c / (MHz.value * 1e6) * 1e9);
        micron.value = roundfive(c / (MHz.value * 1e6) * 1e6);
        fs.value = roundfive(1 / (MHz.value * 1e6) * 1e15);
        ps.value = roundfive(1 / (MHz.value * 1e6) * 1e12);
        K.value = roundfive(h * MHz.value * 1e6 / kB);
      }
    }

    function Kconvert() {
      with (document.conversion) {
        eV.value = roundfive(K.value * kB_eV);
        meV.value = roundfive(K.value * kB_eV * 1e3);
        wavnum.value = roundfive(K.value * 0.69503476);
        THz.value = roundfive(K.value * 20.836);
        MHz.value = roundfive(K.value * 20.836 * 1e6);
        nm.value = roundfive(h * c / (K.value * kB) * 1e9);
        micron.value = roundfive(h * c / (K.value * kB) * 1e6);
        fs.value = roundfive(h / (K.value * kB) * 1e15);
        ps.value = roundfive(h / (K.value * kB) * 1e12);
      }
    }
  </script>
</body>
</html>
