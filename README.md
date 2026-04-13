# RAFI
This is my first website.
<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Modern Calculator</title>

<style>
    *{
        margin:0;
        padding:0;
        box-sizing:border-box;
        font-family: 'Poppins', sans-serif;
    }

    body{
        background: linear-gradient(145deg, #0f0f0f, #1b1b1b);
        height:100vh;
        display:flex;
        justify-content:center;
        align-items:center;
    }

    .calculator{
        width: 350px;
        background: rgba(255,255,255,0.07);
        backdrop-filter: blur(12px);
        border-radius: 25px;
        padding: 20px;
        box-shadow: 0 8px 25px rgba(0,0,0,0.4);
    }

    .display{
        width:100%;
        height:90px;
        background: rgba(255,255,255,0.1);
        border-radius: 15px;
        margin-bottom: 20px;
        padding:20px;
        font-size: 2.2rem;
        color: #fff;
        text-align:right;
        overflow:hidden;
        display:flex;
        align-items:flex-end;
        justify-content:flex-end;
        word-wrap:break-word;
    }

    .buttons{
        display:grid;
        grid-template-columns: repeat(4, 1fr);
        gap:12px;
    }

    button{
        padding:18px;
        font-size:1.4rem;
        background: rgba(255,255,255,0.08);
        border:none;
        border-radius:12px;
        color:#fff;
        transition:0.2s;
        backdrop-filter: blur(10px);
    }

    button:active{
        transform:scale(0.92);
    }

    .operator{
        background: #ff9f0a;
        color:#000;
        font-weight:600;
    }

    .equal{
        grid-column: span 2;
        background:#0a84ff;
        font-weight:700;
    }

    .clear{
        background:#ff453a;
        font-weight:700;
    }
</style>

</head>
<body>

<div class="calculator">
    <div class="display" id="display">0</div>

    <div class="buttons">
        <button class="clear" onclick="clearDisplay()">C</button>
        <button onclick="delChar()">⌫</button>
        <button onclick="press('%')" class="operator">%</button>
        <button onclick="press('/')" class="operator">÷</button>

        <button onclick="press('7')">7</button>
        <button onclick="press('8')">8</button>
        <button onclick="press('9')">9</button>
        <button onclick="press('*')" class="operator">×</button>

        <button onclick="press('4')">4</button>
        <button onclick="press('5')">5</button>
        <button onclick="press('6')">6</button>
        <button onclick="press('-')" class="operator">−</button>

        <button onclick="press('1')">1</button>
        <button onclick="press('2')">2</button>
        <button onclick="press('3')">3</button>
        <button onclick="press('+')" class="operator">+</button>

        <button onclick="press('0')" style="grid-column: span 2">0</button>
        <button onclick="press('.')">.</button>
        <button class="equal" onclick="calculate()">=</button>
    </div>
</div>

<script>
    const display = document.getElementById('display');

    function press(x){
        if(display.innerText === "0") display.innerText = "";
        display.innerText += x;
    }

    function clearDisplay(){
        display.innerText = "0";
    }

    function delChar(){
        display.innerText = display.innerText.slice(0, -1);
        if(display.innerText.length === 0) display.innerText = "0";
    }

    function calculate(){
        try{
            let result = eval(display.innerText.replace('÷','/').replace('×','*'));
            display.innerText = result;
        }catch{
            display.innerText = "Error";
        }
    }
</script>

</body>
</html>
