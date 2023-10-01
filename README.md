﻿<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rectangle Area Calculation</title>
    <link rel="stylesheet" href="Styles/styles.css">
    <script src="Js/script.js"></script>
</head>
<body>

 <div class="container">
    <h1>Calculator</h1>

    <label for="operation">Select an operation:</label>
    <select id="operation" onchange="selectCalculation()">
        <option value="resultDiv">Select an operation</option>
        <option value="addResult">+</option>
        <option value="subtractResult">-</option>
        <option value="multiplyResult">*</option>
        <option value="divideResult">/</option>
        <option value="areaRectangleResult">Area of Rectangle</option>
        <option value="areaSquareResult">Area of Square</option>
        <option value="celsiusToFahrenheitResult">Celsius to Fahrenheit</option>
        <option value="fahrenheitToCelsiusResult">Fahrenheit to Celsius</option>
        <option value="jmdToUsdResult">JMD - USD</option>
        <option value="usdToJmdResult">USD - JMD</option>
        <option value="jmdToPoundResult">JMD - POUND</option>
        <option value="poundToJmdResult">POUND - JMD</option>
    </select>

    <div id="inputFields" style="display: none;">
        <label>Enter value 1:</label>
        <input type="text" id="value1">
        <br>
        <label>Enter value 2:</label>
        <input type="text" id="value2">
        <br> 
        <button onclick="calculate()">Calculate</button>
    </div>

    <div id="resultDiv" class="calculation-div"></div>
    <div id="addResult" class="calculation-div"></div>
    <div id="subtractResult" class="calculation-div"></div>
    <div id="multiplyResult" class="calculation-div"></div>
    <div id="divideResult" class="calculation-div"></div>
    <div id="areaRectangleResult" class="calculation-div"></div>
    <div id="areaSquareResult" class="calculation-div"></div>
    <div id="celsiusToFahrenheitResult" class="calculation-div"></div>
    <div id="fahrenheitToCelsiusResult" class="calculation-div"></div>
    <div id="jmdToUsdResult" class="calculation-div"></div>
    <div id="usdToJmdResult" class="calculation-div"></div>
    <div id="jmdToPoundResult" class="calculation-div"></div>
    <div id="poundToJmdResult" class="calculation-div"></div>
</div>  

</body>
</html>

<script>
const jmdToUsdRate = 155;
const usdToJmdRate = 1 / jmdToUsdRate;
const jmdToPoundRate = 193;
const poundToJmdRate = 1 / jmdToPoundRate;

function selectCalculation() {
    const selectedOperation = document.getElementById('operation').value;

    const calculationDivs = document.getElementsByClassName('calculation-div');
    for (let i = 0; i < calculationDivs.length; i++) {
        calculationDivs[i].style.display = 'none';
    }
    if (selectedOperation !== 'resultDiv') {
        document.getElementById(selectedOperation).style.display = 'block';
        document.getElementById('inputFields').style.display = 'block';
    } else {
        document.getElementById('inputFields').style.display = 'none';
    }
}

function calculate() {
    const selectedOperation = document.getElementById('operation').value;

    if (selectedOperation !== 'resultDiv') {
        const value1 = parseFloat(document.getElementById('value1').value);
        const value2 = parseFloat(document.getElementById('value2').value);
        let result;

        // Perform the calculation based on the selected operation
        if (selectedOperation === 'addResult') {
            result = value1 + value2;
        } else if (selectedOperation === 'subtractResult') {
            result = value1 - value2;
        } else if (selectedOperation === 'multiplyResult') {
            result = value1 * value2;
        } else if (selectedOperation === 'divideResult') {
            result = value1 / value2;
        } else if (selectedOperation === 'areaRectangleResult') {
            result = value1 * value2;
        } else if (selectedOperation === 'areaSquareResult') {
            result = value1 * value1;
        } else if (selectedOperation === 'celsiusToFahrenheitResult') {
            result = (value1 * 9 / 5) + 32;
        } else if (selectedOperation === 'fahrenheitToCelsiusResult') {
            result = (value1 - 32) * 5 / 9;
        } else if (selectedOperation === 'jmdToUsdResult') {
            result = value1 * usdToJmdRate;
        } else if (selectedOperation === 'usdToJmdResult') {
            result = value1 * jmdToUsdRate;
        } else if (selectedOperation === 'jmdToPoundResult') {
            result = value1 * poundToJmdRate;
        } else if (selectedOperation === 'poundToJmdResult') {
            result = value1 * jmdToPoundRate;
        } else {
            result = value1 * jmdToPoundRate;
            }
            
            document.getElementById(selectedOperation).textContent = `Result: ${result}`;
        }
    }
</script>


<style>
.container{
    background-color: gray;
    width: 20rem;
    color: white;
}
</style>

