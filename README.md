#Calculator.html


<!DOCTYPE html>
<html>
<head>
  <title>Calculator</title>
  <style>
    /* CSS styling for the calculator */
    .calculator {
      width: 200px;
      border: 1px solid #ccc;
      padding: 10px;
      text-align: center;
    }

    .calculator input[type="text"] {
      width: 100%;
      margin-bottom: 10px;
      padding: 5px;
    }

    .calculator button {
      width: 48%;
      padding: 5px;
      margin: 2px;
      cursor: pointer;
    }

    .calculator .button-row {
      display: flex;
      justify-content: space-between;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="result" disabled>
    <div class="button-row">
      <button onclick="appendNumber(7)">7</button>
      <button onclick="appendNumber(8)">8</button>
      <button onclick="appendNumber(9)">9</button>
      <button onclick="setOperator('+')">+</button>
    </div>
    <div class="button-row">
      <button onclick="appendNumber(4)">4</button>
      <button onclick="appendNumber(5)">5</button>
      <button onclick="appendNumber(6)">6</button>
      <button onclick="setOperator('-')">-</button>
    </div>
    <div class="button-row">
      <button onclick="appendNumber(1)">1</button>
      <button onclick="appendNumber(2)">2</button>
      <button onclick="appendNumber(3)">3</button>
      <button onclick="setOperator('*')">*</button>
    </div>
    <div class="button-row">
      <button onclick="appendNumber(0)">0</button>
      <button onclick="clearResult()">C</button>
      <button onclick="calculateResult()">=</button>
      <button onclick="setOperator('/')">/</button>
    </div>
  </div>

  <script src="calculator.js"></script>
</body>
</html>



#Calculator.js\



let num1 = '';
let num2 = '';
let operator = '';
let result = '';

function appendNumber(number) {
  if (operator === '') {
    num1 += number;
  } else {
    num2 += number;
  }
  updateDisplay(number);
}

function setOperator(op) {
  operator = op;
  updateDisplay(op);
}

function calculateResult() {
  num1 = parseFloat(num1);
  num2 = parseFloat(num2);

  switch (operator) {
    case '+':
      result = num1 + num2;
      break;
    case '-':
      result = num1 - num2;
      break;
    case '*':
      result = num1 * num2;
      break;
    case '/':
      result = num1 / num2;
      break;
    default:
      result = '';
      break;
  }

  updateDisplay(result);
  resetCalculator();
}

function clearResult() {
  resetCalculator();
  updateDisplay('');
}

function resetCalculator() {
  num1 = '';
  num2 = '';
  operator = '';
  result = '';
}

function updateDisplay(value) {
  document.getElementById('result').value = value;
}
