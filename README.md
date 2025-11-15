<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Simple Calculator</title>
  <style>
    * {
      box-sizing: border-box;
      font-family: "Poppins", sans-serif;
    }

    body {
      background: linear-gradient(135deg, #000000, #060702);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .calculator {
      background: #fff;
      padding: 20px;
      border-radius: 16px;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
      width: 320px;
    }

    .display {
      width: 100%;
      height: 60px;
      border: none;
      background: #f3f3f3;
      border-radius: 8px;
      text-align: right;
      padding: 10px;
      font-size: 1.5em;
      margin-bottom: 15px;
      outline: none;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    button {
      padding: 15px;
      font-size: 1.2em;
      border: none;
      border-radius: 8px;
      background-color: #e0e0e0;
      transition: 0.2s;
      cursor: pointer;
    }

    button:hover {
      background-color: #cfcfcf;
    }

    .operator {
      background-color: #66a6ff;
      color: #fff;
    }

    .operator:hover {
      background-color: #5593ee;
    }

    .equal {
      background-color: #4caf50;
      color: white;
      grid-column: span 2;
    }

    .equal:hover {
      background-color: #45a049;
    }

    .clear {
      background-color: #f44336;
      color: white;
    }

    .clear:hover {
      background-color: #da190b;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" class="display" readonly />

    <div class="buttons">
      <button class="clear" onclick="clearDisplay()">C</button>
      <button onclick="deleteLast()">DEL</button>
      <button class="operator" onclick="appendValue('%')">%</button>
      <button class="operator" onclick="appendValue('/')">÷</button>

      <button onclick="appendValue('7')">7</button>
      <button onclick="appendValue('8')">8</button>
      <button onclick="appendValue('9')">9</button>
      <button class="operator" onclick="appendValue('*')">×</button>

      <button onclick="appendValue('4')">4</button>
      <button onclick="appendValue('5')">5</button>
      <button onclick="appendValue('6')">6</button>
      <button class="operator" onclick="appendValue('-')">−</button>

      <button onclick="appendValue('1')">1</button>
      <button onclick="appendValue('2')">2</button>
      <button onclick="appendValue('3')">3</button>
      <button class="operator" onclick="appendValue('+')">+</button>

      <button onclick="appendValue('0')">0</button>
      <button onclick="appendValue('.')">.</button>
      <button class="equal" onclick="calculateResult()">=</button>
    </div>
  </div>

  <script>
    const display = document.getElementById("display");

    function appendValue(value) {
      display.value += value;
    }

    function clearDisplay() {
      display.value = "";
    }

    function deleteLast() {
      display.value = display.value.slice(0, -1);
    }

    function calculateResult() {
      try {
        display.value = eval(display.value.replace("÷", "/").replace("×", "*"));
      } catch {
        display.value = "Error";
      }
    }
  </script>
</body>
</html>
