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
      --green: #08a100;
      --green-dark: #078700;
      --orange: #f4a300;
      --orange-dark: #df9200;

      --bg: #ececec;
      --surface: #ededed;
      --surface-2: #e7e7e7;

      --ink: #121212;
      --purple: #9221a4;

      --hex-w: 118px;
      --hex-h: 104px;
      --hex-border: 4px;

      --row-overlap: 24px;
      --board-offset: calc(var(--hex-w) / 2);
      --board-width: calc(var(--hex-w) * 5 + var(--board-offset));
    }

    body {
      margin: 0;
      min-height: 100vh;
      font-family: "Tahoma", "Arial", sans-serif;
      background:
        radial-gradient(circle at top, rgba(255,255,255,0.45), transparent 32%),
        linear-gradient(180deg, #efefef 0%, #e6e6e6 100%);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 24px;
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
        0 10px 24px rgba(0, 0, 0, 0.08),
        inset 0 1px 0 rgba(255,255,255,0.9);
      border: 1px solid rgba(0, 0, 0, 0.05);
    }

    .logo-mark {
      width: 22px;
      height: 22px;
      border-radius: 7px;
      overflow: hidden;
      position: relative;
      flex-shrink: 0;
      background:
        linear-gradient(to bottom, var(--green) 0 50%, var(--orange) 50% 100%);
      box-shadow: inset 0 0 0 1px rgba(0,0,0,0.08);
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
      font-size: 30px;
      font-weight: 800;
      line-height: 1;
      color: #262626;
    }

    .frame {
      position: relative;
      display: inline-block;
      overflow: hidden;
      border-radius: 42px;
      padding: 26px 28px;
      background:
        linear-gradient(var(--green), var(--green)) top / 100% 30px no-repeat,
        linear-gradient(var(--green), var(--green)) bottom / 100% 30px no-repeat,
        linear-gradient(var(--orange), var(--orange)) left / 28px 100% no-repeat,
        linear-gradient(var(--orange), var(--orange)) right / 28px 100% no-repeat,
        linear-gradient(180deg, var(--surface) 0%, var(--surface-2) 100%);
      box-shadow:
        0 18px 40px rgba(0, 0, 0, 0.14),
        inset 0 1px 0 rgba(255,255,255,0.45);
    }

    .frame::before {
      content: "";
      position: absolute;
      inset: 10px;
      border-radius: 30px;
      border: 1px solid rgba(0,0,0,0.05);
      pointer-events: none;
    }

    .frame::after {
      content: "";
      position: absolute;
      inset: 0;
      border-radius: inherit;
      background:
        radial-gradient(circle at 12% 12%, rgba(255,255,255,0.20), transparent 18%),
        radial-gradient(circle at 88% 88%, rgba(255,255,255,0.12), transparent 20%);
      pointer-events: none;
    }

    .inner {
      position: relative;
      padding: 26px 28px 30px;
      border-radius: 28px;
      background: transparent;
    }

    .board-wrap {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100%;
    }

    .board {
      width: var(--board-width);
      direction: ltr;
      position: relative;
      margin: 0 auto;
      padding: 6px 0;
    }

    .board::before {
      content: "";
      position: absolute;
      inset: 40px 20px;
      border-radius: 24px;
      background:
        radial-gradient(circle at center, rgba(255,255,255,0.28), transparent 68%);
      filter: blur(10px);
      pointer-events: none;
    }

    .row {
      display: flex;
      width: calc(var(--hex-w) * 5);
      position: relative;
    }

    .row + .row {
      margin-top: calc(var(--row-overlap) * -1);
    }

    .row.offset {
      margin-left: var(--board-offset);
    }

    .hex {
      --fill: #fcfcfc;
      --text: var(--purple);

      position: relative;
      flex: 0 0 var(--hex-w);
      width: var(--hex-w);
      height: var(--hex-h);
      cursor: pointer;
      user-select: none;
      -webkit-tap-highlight-color: transparent;
      transition:
        filter 0.18s ease,
        transform 0.12s ease;
    }

    .hex::before,
    .hex::after {
      content: "";
      position: absolute;
      inset: 0;
      clip-path: polygon(
        50% 0%,
        100% 25%,
        100% 75%,
        50% 100%,
        0% 75%,
        0% 25%
      );
    }

    .hex::before {
      background: var(--ink);
      filter: drop-shadow(0 6px 10px rgba(0,0,0,0.08));
    }

    .hex::after {
      inset: var(--hex-border);
      background: var(--fill);
      box-shadow: inset 0 0 0 1px rgba(255,255,255,0.55);
    }

    .hex span {
      position: absolute;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 1;
      font-size: 28px;
      font-weight: 800;
      color: var(--text);
      line-height: 1;
      text-shadow: 0 1px 0 rgba(255,255,255,0.28);
    }

    .hex.white {
      --fill: #fcfcfc;
      --text: var(--purple);
    }

    .hex.yellow {
      --fill: #f2c230;
      --text: #1a1a1a;
    }

    .hex.green {
      --fill: #42ab68;
      --text: #ffffff;
    }

    .hex.orange {
      --fill: #f5a300;
      --text: #ffffff;
    }

    @media (hover: hover) and (pointer: fine) {
      .hex:hover {
        filter: brightness(1.01);
        transform: translateY(-2px);
      }
    }

    .hex:active {
      transform: scale(0.985);
    }

    @media (max-width: 1100px) {
      :root {
        --hex-w: 98px;
        --hex-h: 86px;
        --hex-border: 3.5px;
        --row-overlap: 20px;
      }

      .logo-text {
        font-size: 25px;
      }

      .frame {
        padding: 22px 22px;
      }

      .inner {
        padding: 22px 20px 24px;
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
        --row-overlap: 15px;
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
        border-radius: 28px;
        padding: 14px;
        background:
          linear-gradient(var(--green), var(--green)) top / 100% 18px no-repeat,
          linear-gradient(var(--green), var(--green)) bottom / 100% 18px no-repeat,
          linear-gradient(var(--orange), var(--orange)) left / 18px 100% no-repeat,
          linear-gradient(var(--orange), var(--orange)) right / 18px 100% no-repeat,
          linear-gradient(180deg, var(--surface) 0%, var(--surface-2) 100%);
      }

      .frame::before {
        inset: 8px;
        border-radius: 18px;
      }

      .inner {
        padding: 14px 12px 18px;
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
        const hex = document.createElement("button");
        hex.type = "button";
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
