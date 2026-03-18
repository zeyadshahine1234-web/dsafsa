<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>حروف مع أحمد</title>

  <style>
    * {
      box-sizing: border-box;
    }

    :root {
      --green: #0aa000;
      --green-dark: #078700;
      --orange: #f5a300;
      --orange-dark: #de9200;
      --bg: #ececec;
      --surface-top: #f3f3f3;
      --surface-bottom: #e8e8e8;
      --ink: #111111;
      --purple: #8f189c;

      --frame-band: 28px;
      --side-band: 28px;

      --hex-w: 118px;
      --hex-h: 104px;
      --hex-border: 4px;
      --row-lift: -24px;
      --row-shift: 57px;
      --hex-overlap: -7px;
    }

    body {
      margin: 0;
      min-height: 100vh;
      background:
        radial-gradient(circle at top, rgba(255,255,255,0.55), transparent 35%),
        linear-gradient(180deg, #eeeeee 0%, #e6e6e6 100%);
      font-family: "Tahoma", "Arial", sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 28px;
      color: #222;
    }

    .page {
      width: fit-content;
      max-width: 100%;
    }

    .header {
      display: flex;
      justify-content: flex-start;
      margin-bottom: 18px;
    }

    .logo {
      display: inline-flex;
      align-items: center;
      gap: 12px;
      padding: 12px 18px;
      border-radius: 20px;
      background: rgba(255, 255, 255, 0.92);
      box-shadow:
        0 10px 24px rgba(0, 0, 0, 0.09),
        inset 0 1px 0 rgba(255,255,255,0.8);
      border: 1px solid rgba(0, 0, 0, 0.05);
      backdrop-filter: blur(4px);
    }

    .logo-mark {
      width: 22px;
      height: 22px;
      border-radius: 7px;
      background:
        linear-gradient(to bottom, var(--green) 0 50%, var(--orange) 50% 100%);
      position: relative;
      overflow: hidden;
      box-shadow: inset 0 0 0 1px rgba(0,0,0,0.08);
      flex-shrink: 0;
    }

    .logo-mark::before,
    .logo-mark::after {
      content: "";
      position: absolute;
      top: 0;
      bottom: 0;
      width: 4px;
      background: var(--orange);
    }

    .logo-mark::before { right: 0; }
    .logo-mark::after { left: 0; }

    .logo-text {
      font-size: 31px;
      font-weight: 800;
      line-height: 1;
      color: #222;
      letter-spacing: 0.2px;
    }

    .frame {
      position: relative;
      display: inline-block;
      padding: 26px 30px;
      border-radius: 42px;
      overflow: hidden;
      background:
        linear-gradient(var(--green), var(--green)) top / 100% var(--frame-band) no-repeat,
        linear-gradient(var(--green), var(--green)) bottom / 100% var(--frame-band) no-repeat,
        linear-gradient(var(--orange), var(--orange)) left / var(--side-band) 100% no-repeat,
        linear-gradient(var(--orange), var(--orange)) right / var(--side-band) 100% no-repeat,
        linear-gradient(180deg, var(--surface-top) 0%, var(--surface-bottom) 100%);
      box-shadow:
        0 18px 38px rgba(0, 0, 0, 0.16),
        inset 0 1px 0 rgba(255,255,255,0.35);
    }

    .frame::before {
      content: "";
      position: absolute;
      inset: 0;
      border-radius: inherit;
      background:
        radial-gradient(circle at 12% 10%, rgba(255,255,255,0.26), transparent 20%),
        radial-gradient(circle at 88% 88%, rgba(255,255,255,0.16), transparent 18%);
      pointer-events: none;
    }

    .frame::after {
      content: "";
      position: absolute;
      inset: 14px;
      border-radius: 30px;
      border: 1px solid rgba(0, 0, 0, 0.05);
      pointer-events: none;
    }

    .inner {
      position: relative;
      border-radius: 30px;
      padding: 28px 34px 34px;
      background: transparent;
    }

    .board-wrap {
      display: flex;
      justify-content: center;
      align-items: center;
      width: fit-content;
      margin: 0 auto;
      position: relative;
    }

    .board-wrap::before {
      content: "";
      position: absolute;
      inset: 18px 10px;
      border-radius: 28px;
      background:
        radial-gradient(circle at center, rgba(255,255,255,0.45), rgba(255,255,255,0) 70%);
      pointer-events: none;
      filter: blur(12px);
    }

    .board {
      direction: ltr;
      display: flex;
      flex-direction: column;
      align-items: center;
      width: fit-content;
      padding: 8px 6px;
      position: relative;
      z-index: 1;
    }

    .row {
      display: flex;
      justify-content: center;
      margin-top: var(--row-lift);
      position: relative;
    }

    .row:first-child {
      margin-top: 0;
    }

    .row.offset {
      transform: translateX(var(--row-shift));
    }

    .hex {
      position: relative;
      width: var(--hex-w);
      height: var(--hex-h);
      margin-left: var(--hex-overlap);
      clip-path: polygon(
        50% 0%,
        100% 25%,
        100% 75%,
        50% 100%,
        0% 75%,
        0% 25%
      );
      background: var(--ink);
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      user-select: none;
      transition:
        transform 0.18s ease,
        filter 0.18s ease,
        box-shadow 0.18s ease;
      z-index: 1;
      box-shadow: 0 8px 14px rgba(0, 0, 0, 0.12);
    }

    .hex:first-child {
      margin-left: 0;
    }

    .hex::before {
      content: "";
      position: absolute;
      inset: var(--hex-border);
      clip-path: polygon(
        50% 0%,
        100% 25%,
        100% 75%,
        50% 100%,
        0% 75%,
        0% 25%
      );
      background: #f9f9f9;
      z-index: 0;
      box-shadow: inset 0 0 0 1px rgba(255,255,255,0.6);
    }

    .hex::after {
      content: "";
      position: absolute;
      inset: calc(var(--hex-border) + 2px);
      clip-path: polygon(
        50% 0%,
        100% 25%,
        100% 75%,
        50% 100%,
        0% 75%,
        0% 25%
      );
      background: linear-gradient(180deg, rgba(255,255,255,0.18), transparent 35%);
      z-index: 0;
      pointer-events: none;
    }

    .hex span {
      position: relative;
      z-index: 1;
      font-size: 28px;
      font-weight: 800;
      color: var(--purple);
      line-height: 1;
      text-shadow: 0 1px 0 rgba(255,255,255,0.35);
    }

    .hex:hover {
      transform: translateY(-3px) scale(1.02);
      filter: brightness(0.99);
      z-index: 3;
      box-shadow: 0 12px 18px rgba(0, 0, 0, 0.16);
    }

    .hex.white::before {
      background: #fcfcfc;
    }

    .hex.yellow::before {
      background: #f2c230;
    }

    .hex.yellow span {
      color: #1d1d1d;
      text-shadow: none;
    }

    .hex.green::before {
      background: #42ab68;
    }

    .hex.green span {
      color: #ffffff;
      text-shadow: none;
    }

    .hex.orange::before {
      background: #f5a300;
    }

    .hex.orange span {
      color: #ffffff;
      text-shadow: none;
    }

    @media (max-width: 1100px) {
      :root {
        --hex-w: 98px;
        --hex-h: 86px;
        --hex-border: 3.5px;
        --row-lift: -20px;
        --row-shift: 48px;
        --hex-overlap: -6px;
        --frame-band: 24px;
        --side-band: 24px;
      }

      .logo-text {
        font-size: 25px;
      }

      .frame {
        padding: 22px 24px;
      }

      .inner {
        padding: 24px 24px 28px;
      }

      .hex span {
        font-size: 23px;
      }
    }

    @media (max-width: 760px) {
      :root {
        --hex-w: 74px;
        --hex-h: 65px;
        --hex-border: 3px;
        --row-lift: -15px;
        --row-shift: 36px;
        --hex-overlap: -5px;
        --frame-band: 18px;
        --side-band: 18px;
      }

      body {
        padding: 14px;
      }

      .logo {
        padding: 10px 14px;
        border-radius: 16px;
      }

      .logo-text {
        font-size: 20px;
      }

      .frame {
        padding: 14px 14px 16px;
        border-radius: 28px;
      }

      .frame::after {
        inset: 9px;
        border-radius: 20px;
      }

      .inner {
        border-radius: 18px;
        padding: 16px 14px 20px;
      }

      .hex span {
        font-size: 18px;
      }
    }
  </style>
</head>
<body>

  <div class="page">
    <div class="header">
      <div class="logo">
        <div class="logo-mark"></div>
        <div class="logo-text">حروف مع أحمد</div>
      </div>
    </div>

    <div class="frame">
      <div class="inner">
        <div class="board-wrap">
          <div class="board" id="board"></div>
        </div>
      </div>
    </div>
  </div>

  <script>
    const letters = [
      "م","ا","ق","س","هـ",
      "ك","ط","ع","و","ل",
      "ف","ن","ص","د","ي",
      "ر","ب","ت","ث","ج",
      "ح","خ","ذ","ز","ش"
    ];

    const colors = ["white", "yellow", "green", "orange"];

    function shuffle(array) {
      const arr = [...array];
      for (let i = arr.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [arr[i], arr[j]] = [arr[j], arr[i]];
      }
      return arr;
    }

    const shuffled = shuffle(letters);

    const rows = [
      shuffled.slice(0, 5),
      shuffled.slice(5, 10),
      shuffled.slice(10, 15),
      shuffled.slice(15, 20),
      shuffled.slice(20, 25)
    ];

    const board = document.getElementById("board");

    rows.forEach((rowLetters, rowIndex) => {
      const row = document.createElement("div");
      row.className = rowIndex % 2 === 1 ? "row offset" : "row";

      rowLetters.forEach(letter => {
        const hex = document.createElement("div");
        hex.className = "hex white";

        const text = document.createElement("span");
        text.textContent = letter;
        hex.appendChild(text);

        let index = 0;

        hex.addEventListener("click", () => {
          hex.classList.remove(colors[index]);
          index = (index + 1) % colors.length;
          hex.classList.add(colors[index]);
        });

        row.appendChild(hex);
      });

      board.appendChild(row);
    });
  </script>

</body>
</html>
