# Standard-Calculator
# index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button class="button clear" onclick="clearDisplay()">C</button>
            <button class="button delete" onclick="deleteLast()">DEL</button>
            <button class="button operator" onclick="appendOperator('%')">%</button>
            <button class="button operator" onclick="appendOperator('/')">/</button>
            <button class="button" onclick="appendNumber('7')">7</button>
            <button class="button" onclick="appendNumber('8')">8</button>
            <button class="button" onclick="appendNumber('9')">9</button>
            <button class="button operator" onclick="appendOperator('*')">*</button>
            <button class="button" onclick="appendNumber('4')">4</button>
            <button class="button" onclick="appendNumber('5')">5</button>
            <button class="button" onclick="appendNumber('6')">6</button>
            <button class="button operator" onclick="appendOperator('-')">-</button>
            <button class="button" onclick="appendNumber('1')">1</button>
            <button class="button" onclick="appendNumber('2')">2</button>
            <button class="button" onclick="appendNumber('3')">3</button>
            <button class="button operator" onclick="appendOperator('+')">+</button>
            <button class="button zero" onclick="appendNumber('0')">0</button>
            <button class="button" onclick="appendNumber('.')">.</button>
            <button class="button equal" onclick="calculateResult()">=</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>
```
# styles.css
```html
/* styles.css */
body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    font-family: Arial, sans-serif;
    background: url('cal.webp') no-repeat center center fixed;
    background-size: cover;
}

.calculator {
    width: 320px;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    background-color: rgba(255, 255, 255, 0.9); /* Semi-transparent background */
}

.display {
    background-color: #333333;
    color: white;
    text-align: right;
    padding: 20px;
    font-size: 2em;
    border-bottom: 1px solid #ccc;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
}

.button {
    padding: 20px;
    font-size: 1.5em;
    border: 1px solid #ccc;
    cursor: pointer;
    transition: background-color 0.3s, color 0.3s;
}

.button:hover {
    background-color: #f0f0f0;
}

.zero {
    grid-column: span 2;
}

.equal {
    background-color: #ff9500;
    color: white;
    grid-row: span 2;
}

.equal:hover {
    background-color: #e68900;
}

.button:not(.equal) {
    background-color: #ffffff;
}

.button:not(.equal):hover {
    background-color: #e0e0e0;
}

.button.operator {
    background-color: #f7b731;
    color: white;
}

.button.operator:hover {
    background-color: #e6a920;
}

.button.clear {
    background-color: #ff3b30;
    color: white;
}

.button.clear:hover {
    background-color: #e63220;
}

.button.delete {
    background-color: #34c759;
    color: white;
}

.button.delete:hover {
    background-color: #28a745;
}
```
# script.js
```html
// script.js
let display = document.getElementById('display');
let currentInput = '';
let operator = null;
let previousInput = '';

function appendNumber(number) {
    if (currentInput.includes('.') && number === '.') return;
    currentInput += number;
    updateDisplay();
}

function appendOperator(op) {
    if (currentInput === '') return;
    if (previousInput !== '') {
        calculateResult();
    }
    operator = op;
    previousInput = currentInput;
    currentInput = '';
}

function clearDisplay() {
    currentInput = '';
    previousInput = '';
    operator = null;
    updateDisplay();
}

function deleteLast() {
    currentInput = currentInput.slice(0, -1);
    updateDisplay();
}

function calculateResult() {
    let result;
    const prev = parseFloat(previousInput);
    const current = parseFloat(currentInput);

    if (isNaN(prev) || isNaN(current)) return;

    switch (operator) {
        case '+':
            result = prev + current;
            break;
        case '-':
            result = prev - current;
            break;
        case '*':
            result = prev * current;
            break;
        case '/':
            result = prev / current;
            break;
        case '%':
            result = prev % current;
            break;
        default:
            return;
    }

    currentInput = result.toString();
    operator = null;
    previousInput = '';
    updateDisplay();
}

function updateDisplay() {
    display.innerText = currentInput || '0';
}
```
# output
![simple cal](https://github.com/PrakashG-2002/Standard-Calculator/assets/144507749/ebe2f505-8c36-4293-92c7-bf96906ed226)


