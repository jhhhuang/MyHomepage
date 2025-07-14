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

    function round_sig(num, sig = 7) {
  if (num === 0) return "0";
  const digits = sig - Math.floor(Math.log10(Math.abs(num))) - 1;
  return Number.parseFloat(num).toPrecision(sig);
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
        MHz.value = round_sig(eV.value / h * 1e-6);
        K.value = round_sig(eV.value / kB_eV);
      }
    }

    function meVconvert() {
      with (document.conversion) {
        eV.value = round_sig(meV.value * 1e-3);
        nm.value = round_sig(h * c / meV.value * 1e9 * 1e3);
        micron.value = round_sig(h * c / meV.value * 1e6 * 1e3);
        wavnum.value = round_sig(meV.value / (h * c * 100) * 1e-3);
        THz.value = round_sig(meV.value / h * 1e-12 * 1e-3);
        fs.value = round_sig(h / meV.value * 1e15 * 1e3);
        ps.value = round_sig(h / meV.value * 1e12 * 1e3);
        MHz.value = round_sig(meV.value / h * 1e-6 * 1e-3);
        K.value = round_sig(meV.value * 1e-3 / kB_eV);
      }
    }

    function nmconvert() {
      with (document.conversion) {
        eV.value = round_sig(h * c / nm.value * 1e9);
        meV.value = round_sig(h * c / nm.value * 1e12);
        micron.value = round_sig(nm.value * 1e-3);
        wavnum.value = round_sig(1 / (nm.value * 1e-7));
        THz.value = round_sig(c / nm.value * 1e-3);
        fs.value = round_sig(nm.value / c * 1e6);
        ps.value = round_sig(nm.value / c * 1e3);
        MHz.value = round_sig(eV.value / h * 1e-6);
        K.value = round_sig(eV.value / kB_eV);
      }
    }

    function micronconvert() {
      with (document.conversion) {
        eV.value = round_sig(h * c / micron.value * 1e6);
        meV.value = round_sig(h * c / micron.value * 1e9);
        nm.value = round_sig(micron.value * 1e3);
        wavnum.value = round_sig(1 / (micron.value * 1e-4));
        THz.value = round_sig(c / micron.value * 1e-6);
        fs.value = round_sig(micron.value / c * 1e9);
        ps.value = round_sig(micron.value / c * 1e6);
        MHz.value = round_sig(eV.value / h * 1e-6);
        K.value = round_sig(eV.value / kB_eV);
      }
    }

    function wavnumconvert() {
      with (document.conversion) {
        eV.value = round_sig(wavnum.value * h * c * 100);
        meV.value = round_sig(wavnum.value * h * c * 100 * 1e3);
        nm.value = round_sig(1e9 / (wavnum.value * 100));
        micron.value = round_sig(1e6 / (wavnum.value * 100));
        THz.value = round_sig(wavnum.value * c * 100 * 1e-12);
        fs.value = round_sig(1 / (wavnum.value * c * 100) * 1e15);
        ps.value = round_sig(1 / (wavnum.value * c * 100) * 1e12);
        MHz.value = round_sig(eV.value / h * 1e-6);
        K.value = round_sig(eV.value / kB_eV);
      }
    }

    function THzconvert() {
      with (document.conversion) {
        eV.value = round_sig(h * THz.value * 1e12);
        meV.value = round_sig(h * THz.value * 1e15);
        nm.value = round_sig(c / THz.value * 1e-3);
        micron.value = round_sig(c / THz.value * 1e-6);
        wavnum.value = round_sig(THz.value * 1e12 / (c * 100));
        fs.value = round_sig(1 / (THz.value * 1e12) * 1e15);
        ps.value = round_sig(1 / (THz.value * 1e12) * 1e12);
        MHz.value = round_sig(THz.value * 1e6);
        K.value = round_sig(eV.value / kB_eV);
      }
    }

    function fsconvert() {
      with (document.conversion) {
        eV.value = round_sig(h / fs.value * 1e15);
        meV.value = round_sig(h / fs.value * 1e18);
        nm.value = round_sig(c * fs.value * 1e-6);
        micron.value = round_sig(c * fs.value * 1e-9);
        wavnum.value = round_sig(1 / (fs.value * c * 100) * 1e15);
        THz.value = round_sig(1 / fs.value);
        ps.value = round_sig(fs.value * 1e-3);
        MHz.value = round_sig(eV.value / h * 1e-6);
        K.value = round_sig(eV.value / kB_eV);
      }
    }

    function psconvert() {
      with (document.conversion) {
        eV.value = round_sig(h / ps.value * 1e12);
        meV.value = round_sig(h / ps.value * 1e15);
        nm.value = round_sig(c * ps.value * 1e-3);
        micron.value = round_sig(c * ps.value * 1e-6);
        wavnum.value = round_sig(1 / (ps.value * c * 100) * 1e12);
        THz.value = round_sig(1 / ps.value);
        fs.value = round_sig(ps.value * 1e3);
        MHz.value = round_sig(eV.value / h * 1e-6);
        K.value = round_sig(eV.value / kB_eV);
      }
    }

    function MHzconvert() {
      with (document.conversion) {
        THz.value = round_sig(MHz.value * 1e-6);
        eV.value = round_sig(h * MHz.value * 1e6);
        meV.value = round_sig(h * MHz.value * 1e9);
        wavnum.value = round_sig((h * MHz.value * 1e6) / (h * c * 100));
        nm.value = round_sig(c / (MHz.value * 1e6) * 1e9);
        micron.value = round_sig(c / (MHz.value * 1e6) * 1e6);
        fs.value = round_sig(1 / (MHz.value * 1e6) * 1e15);
        ps.value = round_sig(1 / (MHz.value * 1e6) * 1e12);
        K.value = round_sig(MHz.value * 1e6 * h / kB); 
      }
    }

    function Kconvert() {
      with (document.conversion) {
        eV.value = round_sig(K.value * kB_eV);
        meV.value = round_sig(K.value * kB_eV * 1e3);
        wavnum.value = round_sig(K.value * kB / (h * c * 100));
        THz.value = round_sig(K.value * kB / h * 1e-12);
        MHz.value = round_sig(K.value * kB / h * 1e-6);
        nm.value = round_sig(h * c / (K.value * kB) * 1e9);
        micron.value = round_sig(h * c / (K.value * kB) * 1e6);
        fs.value = round_sig(h / (K.value * kB) * 1e15);
        ps.value = round_sig(h / (K.value * kB) * 1e12);
      }
    }

    }
  </script>
</body>
</html>
