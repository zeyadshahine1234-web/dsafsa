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
      --panel: #f7f7f7;
      --ink: #111111;
      --purple: #8f189c;

      --hex-w: 118px;
      --hex-h: 104px;
      --hex-border: 4px;
      --row-lift: -24px;
      --row-shift: 60px;
    }

    body {
      margin: 0;
      min-height: 100vh;
      background: var(--bg);
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
      border-radius: 18px;
      background: rgba(255, 255, 255, 0.88);
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08);
      border: 1px solid rgba(0, 0, 0, 0.05);
      backdrop-filter: blur(4px);
    }

    .logo-mark {
      width: 20px;
      height: 20px;
      border-radius: 6px;
      background:
        linear-gradient(to bottom, var(--green) 0 50%, var(--orange) 50% 100%);
      position: relative;
      overflow: hidden;
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
      color: #2a2a2a;
    }

    .frame {
      position: relative;
      display: inline-block;
      padding: 34px;
      border-radius: 42px;
      background:
        linear-gradient(to right,
          var(--orange) 0%,
          var(--orange) 10%,
          var(--green) 10%,
          var(--green) 90%,
          var(--orange) 90%,
          var(--orange) 100%);
      box-shadow: 0 16px 34px rgba(0, 0, 0, 0.14);
    }

    .frame::before {
      content: "";
      position: absolute;
      inset: 0;
      border-radius: 42px;
      background:
        linear-gradient(to bottom,
          var(--green) 0 26px,
          transparent 26px calc(100% - 26px),
          var(--green) calc(100% - 26px) 100%);
      pointer-events: none;
    }

    .inner {
      position: relative;
      background: var(--panel);
      border-radius: 34px;
      padding: 34px 46px 42px;
      box-shadow:
        inset 0 1px 0 rgba(255,255,255,0.9),
        0 6px 16px rgba(0,0,0,0.05);
    }

    .board-wrap {
      display: flex;
      justify-content: center;
      align-items: center;
      width: fit-content;
      margin: 0 auto;
    }

    .board {
      direction: ltr;
      display: flex;
      flex-direction: column;
      align-items: center;
      width: fit-content;
      padding: 6px;
    }

    .row {
      display: flex;
      justify-content: center;
      margin-top: var(--row-lift);
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
      margin-left: -6px;
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
      transition: transform 0.15s ease, filter 0.15s ease;
      z-index: 1;
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
      background: #fcfcfc;
      z-index: 0;
    }

    .hex span {
      position: relative;
      z-index: 1;
      font-size: 26px;
      font-weight: 800;
      color: var(--purple);
      line-height: 1;
    }

    .hex:hover {
      transform: translateY(-2px);
      filter: brightness(0.98);
      z-index: 3;
    }

    .hex.white::before {
      background: #fcfcfc;
    }

    .hex.yellow::before {
      background: #f2c230;
    }

    .hex.yellow span {
      color: #1c1c1c;
    }

    .hex.green::before {
      background: #42ab68;
    }

    .hex.green span {
      color: #ffffff;
    }

    .hex.orange::before {
      background: #f5a300;
    }

    .hex.orange span {
      color: #ffffff;
    }

    @media (max-width: 1100px) {
      :root {
        --hex-w: 98px;
        --hex-h: 86px;
        --hex-border: 3.5px;
        --row-lift: -20px;
        --row-shift: 50px;
      }

      .logo-text {
        font-size: 25px;
      }

      .frame {
        padding: 24px;
      }

      .inner {
        padding: 26px 30px 32px;
      }

      .hex span {
        font-size: 22px;
      }
    }

    @media (max-width: 760px) {
      :root {
        --hex-w: 74px;
        --hex-h: 65px;
        --hex-border: 3px;
        --row-lift: -15px;
        --row-shift: 38px;
      }

      body {
        padding: 14px;
      }

      .logo {
        padding: 10px 14px;
      }

      .logo-text {
        font-size: 20px;
      }

      .frame {
        padding: 16px;
        border-radius: 26px;
      }

      .frame::before {
        border-radius: 26px;
      }

      .inner {
        border-radius: 20px;
        padding: 18px 18px 22px;
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
      "ة","ط","ع","و","ل",
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
