---
title: "Singapore Number Plate Checksum Calculator"
description: "Free Singapore vehicle registration plate checksum calculator. Enter your prefix and serial number (e.g. SCJ 2000) and instantly get the last alphabet letter, with the full LTA formula explained."

cascade:
  showReadingTime: false
  showWordCount: false
  showRelated: false
  showDate: false
  showAuthor: false
  showViews: false
  showEdit: false
  showZenMode: false
---
<link
  rel="stylesheet"
  href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&display=swap"
/>
<style>
  .pchk {
    color: #fff;
    font-family: "JetBrains Mono", ui-monospace, "SF Mono", Menlo, monospace;
    line-height: 1.6;
  }
  .pchk .sub { color: #9ca3af; font-size: 15px; max-width: 56ch; }
  .pchk .tool { margin: 32px 0; padding: 24px; border: 1px solid #23262f; border-radius: 12px; background: #10121a; }
  .pchk label { display: block; font-size: 12px; color: #9ca3af; margin-bottom: 6px; letter-spacing: 1px; }
  .pchk .row { display: flex; gap: 10px; flex-wrap: wrap; }
  .pchk input {
    flex: 1; min-width: 200px; padding: 14px 16px; font: inherit; font-size: 18px;
    background: #0a0b10; color: #fff; border: 1px solid #2a2e3a; border-radius: 8px;
    text-transform: uppercase; letter-spacing: 3px;
  }
  .pchk input:focus { outline: none; border-color: #a78bfa; }
  .pchk button {
    padding: 14px 24px; font: inherit; font-weight: 700; cursor: pointer;
    background: #a78bfa; color: #0a0b10; border: 0; border-radius: 8px;
  }
  .pchk button:hover { background: #c4b5fd; }
  .pchk .result { margin-top: 20px; display: none; }
  .pchk .result.show { display: block; }
  .pchk .plate {
    display: inline-block; padding: 14px 26px; background: #f5d400; color: #111;
    font-size: 30px; font-weight: 700; border-radius: 6px; letter-spacing: 2px;
  }
  .pchk .plate .suffix { color: #7c3aed; }
  .pchk .verdict { margin-top: 12px; font-size: 14px; }
  .pchk .verdict.ok { color: #4ade80; }
  .pchk .verdict.warn { color: #fbbf24; }
  .pchk .verdict.err { color: #f87171; }
  .pchk .steps { margin-top: 16px; font-size: 13px; color: #9ca3af; }
  .pchk .steps code { color: #c4b5fd; }
  .pchk p, .pchk li { font-size: 15px; color: #d1d5db; }
  .pchk ul { padding-left: 22px; margin: 10px 0; }
  .pchk table { border-collapse: collapse; width: 100%; margin: 14px 0; font-size: 13px; }
  .pchk th, .pchk td { border: 1px solid #23262f; padding: 8px 10px; text-align: left; }
  .pchk th { color: #a78bfa; }
  .pchk .cta {
    margin: 40px 0 0; padding: 24px; border: 1px solid #a78bfa33;
    border-radius: 12px; background: linear-gradient(135deg, #14101f, #10121a);
  }
  .pchk .cta a.btn {
    display: inline-block; margin-top: 12px; padding: 12px 22px; background: #22c55e;
    color: #04110a; font-weight: 700; text-decoration: none; border-radius: 8px;
  }
  .pchk details { border: 1px solid #23262f; border-radius: 8px; padding: 12px 16px; margin: 8px 0; }
  .pchk summary { cursor: pointer; font-weight: 700; font-size: 15px; }
  .pchk details p { margin-top: 10px; }
</style>

<div class="pchk">
<p class="sub">Every Singapore vehicle plate ends with a letter worked out from the prefix and serial number. Enter yours, e.g. <strong>SCJ 2000</strong>, and get the last alphabet instantly.</p>

<section class="tool" aria-label="Plate checksum calculator">
  <label for="pchk-plate">VEHICLE REGISTRATION NUMBER</label>
  <div class="row">
    <input id="pchk-plate" type="text" placeholder="SCJ 2000" autocomplete="off" maxlength="10" inputmode="text">
    <button id="pchk-go" type="button">CHECKSUM</button>
  </div>
  <div class="result" id="pchk-result">
    <div class="plate" id="pchk-plate-out"></div>
    <p class="verdict" id="pchk-verdict"></p>
    <p class="steps" id="pchk-steps"></p>
  </div>
</section>

<h2>How the checksum is calculated</h2>
<p>The Land Transport Authority derives the last letter from the registration number so mistyped or misread plates can be detected:</p>
<ul>
  <li>Take the <strong>last two letters</strong> of the prefix and convert them to numbers (A = 1 … Z = 26). A one-letter prefix counts as 0 plus that letter.</li>
  <li>Write the serial number as <strong>four digits</strong> with leading zeros.</li>
  <li>Multiply the six figures by <code>9, 4, 5, 4, 3, 2</code> and add the results.</li>
  <li>Divide by <strong>19</strong>; the remainder selects the letter from the table below.</li>
</ul>
<table>
  <tr><th>Remainder</th><td>0</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td><td>9</td></tr>
  <tr><th>Letter</th><td>A</td><td>Z</td><td>Y</td><td>X</td><td>U</td><td>T</td><td>S</td><td>R</td><td>P</td><td>M</td></tr>
  <tr><th>Remainder</th><td>10</td><td>11</td><td>12</td><td>13</td><td>14</td><td>15</td><td>16</td><td>17</td><td>18</td><td></td></tr>
  <tr><th>Letter</th><td>L</td><td>K</td><td>J</td><td>H</td><td>G</td><td>E</td><td>D</td><td>C</td><td>B</td><td></td></tr>
</table>
<p>Only 19 letters are needed, so <strong>F, I, N, O, Q, V and W never appear</strong> as the last letter of a Singapore plate.</p>
<p><strong>Example: SCJ 2000.</strong> C = 3, J = 10, digits 2, 0, 0, 0. Then 3×9 + 10×4 + 2×5 + 0 + 0 + 0 = 77. 77 ÷ 19 leaves remainder 1, and position 1 in the table is <strong>Z</strong>. The full plate is SCJ 2000 Z.</p>

<h2>Frequently asked questions</h2>
<details>
  <summary>Why does my plate have a letter at the end?</summary>
  <p>It is a check character, like the last digit of an IC number. If a warden or camera system misreads one character of your plate, the checksum no longer adds up and the error is detected.</p>
</details>
<details>
  <summary>Which letters are never used as the last letter?</summary>
  <p>F, I, N, O, Q, V and W. The remainder of the division is always 0 to 18, mapping to only 19 of the 26 letters.</p>
</details>
<details>
  <summary>Do government or event vehicles have a checksum letter?</summary>
  <p>No. Special government vehicle plates and event vehicle plates skip the checksum letter entirely.</p>
</details>
<details>
  <summary>I ordered a custom 3D plate. Do the letters still need to follow this?</summary>
  <p>The registration number itself is whatever LTA assigned, but the physical letters and numbers on your plate must meet OneMotoring size standards. Our 3D-printed plates are precision-cut to the 70 mm × 50 mm × 10 mm specification.</p>
</details>

<section class="cta">
  <h2 style="margin-top:0">Want your plates to stand out?</h2>
  <p>We craft Singapore's first 3D-printed number plates, in 15+ finishes, made in about a working day. Text us your registration number and we'll take it from there.</p>
  <a class="btn" href="https://wa.me/6588261189?text=Hi%20Sean%2C%20I%20used%20your%20checksum%20tool%20and%20want%203D%20plates%20for%20my%20car%3A">WhatsApp us on +65 8826 1189</a>
</section>
</div>

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "WebApplication",
      "name": "Singapore Number Plate Checksum Calculator",
      "url": "https://www.alisontdesign.com/plate-checksum/",
      "applicationCategory": "UtilityApplication",
      "operatingSystem": "Any",
      "offers": { "@type": "Offer", "price": "0", "priceCurrency": "SGD" },
      "description": "Calculates the checksum letter at the end of a Singapore vehicle registration plate from the prefix and serial number.",
      "creator": { "@type": "Organization", "name": "AlisonT Design Pte. Ltd.", "url": "https://www.alisontdesign.com" }
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        { "@type": "Question", "name": "Why does my plate have a letter at the end?", "acceptedAnswer": { "@type": "Answer", "text": "It is a check character worked out from the prefix and serial number, so mistyped or misread plates are detected." } },
        { "@type": "Question", "name": "Which letters are never used as the last letter of a Singapore plate?", "acceptedAnswer": { "@type": "Answer", "text": "F, I, N, O, Q, V and W, because the checksum remainder only maps to 19 letters." } },
        { "@type": "Question", "name": "How is the Singapore plate checksum calculated?", "acceptedAnswer": { "@type": "Answer", "text": "Take the last two prefix letters as numbers A=1 to Z=26 plus the 4-digit serial, multiply by 9,4,5,4,3,2, sum, divide by 19, and the remainder picks the letter from A Z Y X U T S R P M L K J H G E D C B." } },
        { "@type": "Question", "name": "Do government vehicles have a checksum letter?", "acceptedAnswer": { "@type": "Answer", "text": "No. Special government and event vehicle plates have no checksum letter." } }
      ]
    }
  ]
}
</script>
<script>
(function () {
  var TABLE = "AZYXUTSRPMLKJHGEDCB";
  var W = [9, 4, 5, 4, 3, 2];
  function checksum(prefix, serial) {
    var letters = prefix.length === 1 ? " " + prefix : prefix.slice(-2);
    var f = letters.split("").map(function (c) { return c === " " ? 0 : c.charCodeAt(0) - 64; });
    var s = serial.padStart(4, "0");
    for (var i = 0; i < 4; i++) f.push(parseInt(s[i], 10));
    var total = f.reduce(function (a, n, i) { return a + n * W[i]; }, 0);
    return { letter: TABLE[total % 19], total: total, remainder: total % 19 };
  }
  function show(cls, txt, steps) {
    var v = document.getElementById("pchk-verdict");
    v.className = "verdict " + cls;
    v.textContent = txt;
    document.getElementById("pchk-steps").innerHTML = steps || "";
    document.getElementById("pchk-result").classList.add("show");
  }
  function run() {
    var raw = document.getElementById("pchk-plate").value.trim().toUpperCase().replace(/\s+/g, "");
    var out = document.getElementById("pchk-plate-out");
    if (!raw) return;
    var m = raw.match(/^([A-Z]{1,3})(\d{1,4})([A-Z]?)$/);
    var fixed = null;
    if (!m) {
      fixed = raw.replace(/I/g, "1").replace(/L/g, "1").replace(/O/g, "0").replace(/Q/g, "0");
      m = fixed.match(/^([A-Z]{1,3})(\d{1,4})([A-Z]?)$/);
    }
    if (!m) {
      out.textContent = "???";
      return show("err", "Could not read that plate. Format: 1–3 letters then 1–4 digits, e.g. SCJ 2000.", "");
    }
    var prefix = m[1], serial = m[2], given = m[3];
    var typoNote = (fixed && fixed !== raw) ? "Read as " + fixed + " (typo corrected). " : "";
    if (/[IO]/.test(prefix)) {
      out.textContent = prefix + " " + serial;
      return show("err", "I and O are never used in Singapore plate prefixes — they are probably the digits 1 and 0.", "");
    }
    var r = checksum(prefix, serial);
    out.innerHTML = prefix + " " + serial + ' <span class="suffix">' + r.letter + "</span>";
    var letters = prefix.length === 1 ? [0, prefix.charCodeAt(0) - 64] : [prefix.slice(-2).charCodeAt(0) - 64, prefix.slice(-1).charCodeAt(0) - 64];
    var d = serial.padStart(4, "0").split("").map(Number);
    var calc = letters[0] + "×9 + " + letters[1] + "×4 + " + d[0] + "×5 + " + d[1] + "×4 + " + d[2] + "×3 + " + d[3] + "×2 = " + r.total + "; " + r.total + " ÷ 19 remainder <code>" + r.remainder + "</code> → letter <code>" + r.letter + "</code>.";
    if (given && given !== r.letter) {
      show("err", typoNote + "Checksum mismatch: " + prefix + " " + serial + " should end in " + r.letter + ", not " + given + ".", calc);
    } else if (given) {
      show("ok", typoNote + "Valid plate. The checksum " + given + " checks out.", calc);
    } else {
      show("ok", typoNote + "The full registration number is " + prefix + " " + serial + " " + r.letter + ".", calc);
    }
  }
  document.getElementById("pchk-go").addEventListener("click", run);
  document.getElementById("pchk-plate").addEventListener("keydown", function (e) { if (e.key === "Enter") run(); });
})();
</script>
