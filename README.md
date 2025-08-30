# Scientific-Calculator
Scientific Calculator with multi-line display, ideal for students and professionals. Features trigonometric, logarithmic, statistical, and complex functions, plus equation solving and memory keys. Portable, reliable, and perfect for math, science, and engineering tasks.
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Advanced Scientific Calculator</title>
  <style>
    :root {
      --bg: linear-gradient(145deg, #0f2027, #203a43, #2c5364);
      --glass: rgba(255, 255, 255, 0.08);
      --highlight: #4caf50;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: var(--bg);
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 20px;
    }

    .calculator {
      background: var(--glass);
      backdrop-filter: blur(15px);
      border-radius: 20px;
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
      width: 420px;
      padding: 20px;
    }

    .display {
      width: 100%;
      background: rgba(255, 255, 255, 0.1);
      border: none;
      padding: 20px;
      font-size: 1.8rem;
      color: white;
      border-radius: 10px;
      margin-bottom: 20px;
      text-align: right;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 10px;
    }

    button {
      padding: 15px;
      font-size: 1.1rem;
      border: none;
      border-radius: 12px;
      background-color: rgba(255, 255, 255, 0.12);
      color: white;
      cursor: pointer;
      transition: 0.2s;
    }

    button:hover {
      background-color: rgba(255, 255, 255, 0.25);
    }

    .equal {
      background-color: var(--highlight);
      grid-column: span 2;
      color: white;
    }

    .clear {
      background-color: #f44336;
    }

    .func {
      background-color: #607d8b;
    }

    @media (max-width: 500px) {
      .calculator {
        width: 100%;
      }

      button {
        padding: 12px;
        font-size: 1rem;
      }

      .display {
        font-size: 1.5rem;
      }
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" class="display" disabled placeholder="0">
    <div class="buttons">
      <!-- Row 1 -->
      <button class="func" onclick="append('Math.PI')">π</button>
      <button class="func" onclick="append('Math.E')">e</button>
      <button class="func" onclick="append('(')">(</button>
      <button class="func" onclick="append(')')">)</button>
      <button class="clear" onclick="clearDisplay()">C</button>

      <!-- Row 2 -->
      <button class="func" onclick="append('Math.sqrt(')">√</button>
      <button class="func" onclick="append('Math.pow(')">xʸ</button>
      <button class="func" onclick="append('Math.pow('); append(',2')">x²</button>
      <button class="func" onclick="append('Math.exp(')">eˣ</button>
      <button onclick="deleteLast()">⌫</button>

      <!-- Row 3 -->
      <button onclick="append('7')">7</button>
      <button onclick="append('8')">8</button>
      <button onclick="append('9')">9</button>
      <button onclick="append('/')">÷</button>
      <button class="func" onclick="append('Math.log10(')">log</button>

      <!-- Row 4 -->
      <button onclick="append('4')">4</button>
      <button onclick="append('5')">5</button>
      <button onclick="append('6')">6</button>
      <button onclick="append('*')">×</button>
      <button class="func" onclick="append('Math.log(')">ln</button>

      <!-- Row 5 -->
      <button onclick="append('1')">1</button>
      <button onclick="append('2')">2</button>
      <button onclick="append('3')">3</button>
      <button onclick="append('-')">−</button>
      <button class="func" onclick="append('Math.sin(')">sin</button>

      <!-- Row 6 -->
      <button onclick="append('0')">0</button>
      <button onclick="append('.')">.</button>
      <button onclick="append('+')">+</button>
      <button class="equal" onclick="calculate()">=</button>
      <button class="func" onclick="append('Math.cos(')">cos</button>

      <!-- Row 7 -->
      <button class="func" onclick="append('Math.tan(')">tan</button>
    </div>
  </div>

  <script>
    const display = document.getElementById('display');

    function append(val) {
      display.value += val;
    }

    function clearDisplay() {
      display.value = '';
    }

    function deleteLast() {
      display.value = display.value.slice(0, -1);
    }

    function calculate() {
      try {
        const result = eval(display.value);
        display.value = result;
      } catch (e) {
        display.value = 'Error';
      }
    }

    // Optional: Keyboard support
    document.addEventListener('keydown', (e) => {
      const allowedKeys = '0123456789.+-*/()'.split('');
      if (allowedKeys.includes(e.key)) {
        append(e.key);
      } else if (e.key === 'Enter') {
        e.preventDefault();
        calculate();
      } else if (e.key === 'Backspace') {
        deleteLast();
      } else if (e.key === 'Escape') {
        clearDisplay();
      }
    });
  </script>
</body>
</html>
