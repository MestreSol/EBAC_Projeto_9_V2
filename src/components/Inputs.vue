<script setup lang="ts">
import { ref } from 'vue';
import LCD from './LCD.vue'; // Importando o componente LCD

let conta = ref(''); // Variável reativa para a conta

let isShift = ref(false);
let isAlpha = ref(false);
let isMemory = false;
let isOn = false;
let isInsertX = false;
let isDegree = false;
let isRadianus = false;
let isG = false;
let isFIX = false;
let isSCI = false;
let isE = false;
let isi = false;
let is45graus = false;
let isDown = false;

const lcdDisplay = ref([]); // Variável reativa para o LCD como uma lista de textos

function Shift() {
    isShift.value = !isShift.value;
    lcdDisplay.value = [`Is Shift: ${isShift.value}`];
    console.log(lcdDisplay.value);
}

function Alpha() {
    isAlpha.value = !isAlpha.value;
    lcdDisplay.value = [`Is Alpha: ${isAlpha.value}`];
    console.log(lcdDisplay.value);
}

function Menu() {
    lcdDisplay.value = ["Menu displayed on LCD"];
    console.log(lcdDisplay.value);
}

function On() {
    lcdDisplay.value = [ "LCD turned on" ];
    console.log(lcdDisplay.value);
}

function Option() {
    lcdDisplay.value = [
        "1: Função Hiperból",
        "2: Unidade Angular",
        "3: Simb Engenharia"
    ];
    const optionKeyHandler = (event) => {
        const keyName = event.key;
        switch (keyName) {
            case '1':
                lcdDisplay.value = [
                    "1: sinh",
                    "2: cosh",
                    "3: tanh",
                    "4: sinh^-1",
                    "5: cosh^-1",
                    "6: tanh^-1"
                ];
                document.addEventListener('keydown', hyperbolicKeyHandler);
                break;
            case '2':
                lcdDisplay.value = [
                    "1: Graus",
                    "2: Radianos",
                    "3: Grados"
                ];
                break;
            case '3':
                lcdDisplay.value = [
                    "1: m",
                    "2: cm",
                    "3: mm"
                ];
                break;
            default:
                lcdDisplay.value = ["Opção inválida"];
        }
        console.log(lcdDisplay.value);
        // Remove o evento
        document.removeEventListener('keydown', optionKeyHandler);
    };

    document.addEventListener('keydown', optionKeyHandler);
    console.log(lcdDisplay.value);
}

function Calc() {
    lcdDisplay.value.push("Calculation mode");
    console.log(lcdDisplay.value);
}

function integral() {
    lcdDisplay.value.push("Integral mode");
    console.log(lcdDisplay.value);
}

function x() {
    lcdDisplay.value.push("Variable x");
    console.log(lcdDisplay.value);
}
</script>

<template>
    <div>
        <ul class="display-tools">
            <li :class="{ active: isShift }" id="Shift">⇑</li>
            <li :class="{ active: isAlpha }" id="Alpha">α</li>
            <li :class="{active: isMemory}" id="Memory">Θ</li>
            <li :class="{active: isOn }" id="On">Ο</li>
            <li :class="{active: isInsertX}" id="insertX">~X</li>
            <li :class="{active: isDegree}" id="Degree">D</li>
            <li :class="{active: isRadianus}" id="Radianus">R</li>
            <li :class="{active: isG}" id="G">G</li>
            <li :class="{active: isFIX} " id="FIX">FIX</li>
            <li :class="{active: isSCI } " id="SCI">SCI</li>
            <li :class="{active: isE} " id="E">E</li>
            <li :class="{active: isi}" id="i">i</li>
            <li :class="{active: is45graus}" id="45graus">⋞</li>
            <li :class="{active: isDown}" id="down">⇓</li>
        </ul>
    </div>
    <div class="tela">
        <LCD :display="lcdDisplay" /> <!-- Passando a lista diretamente como propriedade -->
    </div>
    <div class="row function">
        <button @click="Shift">Shift</button>
        <button @click="Alpha">Alpha</button>
        <button @click="Menu">Menu</button>
        <button @click="On">On</button>
    </div>
    <div class="row operation">
        <button @click="Option">Option</button>
        <button @click="Calc">Calc</button>
        <button @click="integral">∬</button>
        <button @click="x">x</button>
    </div>
    <div class="row operation">
        <button @click="diveder">/</button>
        <button @click="srqt">√</button>
        <button @click="pow">^</button>
        <button @click="powx">^x</button>
        <button @click="log">log</button>
        <button @click="ln">ln</button>
    </div>
    <div class="row operation">
        <button @click="negative">(-)</button>
        <button @click="line">° ' "</button>
        <button @click="pownegative">^-1</button>
        <button @click="sin">sin</button>
        <button @click="cos">cos</button>
        <button @click="tan">tan</button>
    </div>
    <div class="row operation">
        <button @click="sto">STO</button>
        <button @click="ENG">ENG</button>
        <button @click="parentes">(</button>
        <button @click="parentesReverso">)</button>
        <button @click="SD">S⇹D</button>
        <button @click="MPlus">M+</button>
    </div>
    <div class="row numeric">
        <button @click="seven">7</button>
        <button @click="eight">8</button>
        <button @click="nine">9</button>
        <button @click="del">DEL</button>
        <button @click="AC">AC</button>
    </div>
    <div class="row numeric">
        <button @click="four">4</button>
        <button @click="five">5</button>
        <button @click="six">6</button>
        <button @click="mult">x</button>
        <button @click="div">/</button>
        </div> 
        <div class="row numeric">
        <button @click="one">1</button>
        <button @click="two">2</button>
        <button @click="three">3</button>
        <button @click="sum">+</button>
        <button @click="sub">-</button>
        </div>
        <div class="row numeric">
        <button @click="zero">0</button>
        <button @click="dot">.</button>
        <button @click="exp">EXP</button>
        <button @click="ans">ANS</button>
        <button @click="equal">=</button>
        </div>
</template>

<style lang="css">
.lcd{
    display:none;
}

.enable{
    display: flex;
    justify-content: center;
}
    .row{
        display: flex;
        justify-content: space-between;
        margin-top: 10px;
    }
    .function button{
        width: 50px;
        height: 50px;
        border-radius: 50%;
        background-color: #f2f2f2;
        border: 1px solid #ccc;
        font-size: 20px;
        font-size: small;
    }
    .function button:hover{
        background-color: #ccc;
    }
    .function button:active{
        background-color: #999;
    }
    .function button:focus{
        outline: none;
    }
    .tela{
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f2f2f2;
  border: 1px solid #ccc;
  border-radius: 10px;
  width: 250px;
  height: 100px;
  margin: 0 auto;
  top:0px;
  
}
    .operation button{
        width: 50px;
        height: 25px;
        background-color: #000;
        border: 1px solid #000;
        font-size: 20px;
        font-size: small;
        color: #fff;
    }

    .operation button:hover{
        background-color: #333;
    }

    .operation button:active{
        background-color: #666;
    }

    .operation button:focus{
        outline: none;
    }

    .numeric button{
        width: 50px;
        height: 50px;
        background-color: #f2f2f2;
        border: 1px solid #ccc;
        font-size: 20px;
        font-size: small;
    }

    .numeric button:hover{
        background-color: #ccc;
    }

    .numeric button:active{
        background-color: #999;
    }

    .numeric button:focus{
        outline: none;
    }

    .numeric button:active{
        background-color: #999;
    }

    
.display-tools {
    display: flex;
    justify-content: space-between;
    width: 100%;
    padding: 0 10px;
    margin-bottom: 10px;
    align-items: center;
}

.display-tools li {
    list-style: none;
    color: white;
    cursor: pointer;
}

.display-tools li.active {
    color: black;
}

</style>