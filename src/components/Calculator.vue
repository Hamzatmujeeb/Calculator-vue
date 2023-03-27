<script>
export default {
  data() {
    return {
      output: "0",
    };
  },
  methods: {
    clearDisplay() {
      this.output = "0";
    },
    backspace() {
      if (this.output.length > 1) {
        this.output = this.output.slice(0, -1);
      } else {
        this.output = "0";
      }
    },
    insertValue(value) {
  if (this.output === "0") {
    this.output = "Math.sqrt(0)";
  } else if (value === "Math.sqrt(") {
    this.output = value + this.output + ")";
  } else {
    this.output += value;
  }
},
    insertValue(value) {
      if (this.output === "0") {
        this.output = value;
      } else {
        this.output += value;
      }
    },
    calculate() {
      try {
        this.output = eval(this.output);
      } catch (error) {
        this.output = "Error";
      }
    },
  },
};
</script>


<template>
 <body>
  <div class="calculator" id="app">
    <div class="display">
     <input type="text" id="result" placeholder="0" readonly v-model="output">
    </div>
    <div class="buttons">
      <button class="clear" @click="clearDisplay">C</button>
      <button class="backspace" @click="backspace">&larr;</button>
      <button class="operator" @click="insertValue('%')">%</button>
      <button class="operator" @click="insertValue('/')">&divide;</button>
      <button class="number"   @click="insertValue('7')">7</button>
      <button class="number" @click="insertValue('8')">8</button>
      <button class="number" @click="insertValue('9')">9</button>
      <button class="operator" @click="insertValue('*')">*</button>
      <button class="number" @click="insertValue('4')">4</button>
      <button class="number" @click="insertValue('5')">5</button>
      <button class="number" @click="insertValue('6')">6</button>
      <button class="operator" @click="insertValue('-')">-</button>
      <button class="number" @click="insertValue('1')">1</button>
      <button class="number" @click="insertValue('2')">2</button>
      <button class="number" @click="insertValue('3')">3</button>
      <button class="operator" @click="insertValue('+')">+</button>
      <button class="number" @click="insertValue('.')">.</button>
      <button class="number" @click="insertValue('0')">0</button>
      <button class="operator" @click="insertValue('Math.sqrt(')">√</button>
      <button class="equals" @click="calculate">=</button>
  </div>
  </div>
 </body>
</template>

<style scoped>
.calculator {
  max-width: 500px;
  margin:100px auto;
  background-color: #f2f2f2;
  border-radius: 5px;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.display {
  margin-bottom: 10px;
}

.display input[type="text"] {
  font-size: 2em;
  width: 100%;
  text-align: right;
  padding: 10px;
  border: none;
  outline: none;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 10px;
}

button {
  font-size: 1.5em;
  padding: 10px;
  border: none;
  outline: none;
  border-radius: 5px;
  cursor: pointer;
}

.number {
  background-color: #d3d3d3;
  color: #000;
}

.operator {
  background-color: #ff9800;
  color: #fff;
}

.equals {
  background-color: #4caf50;
  color: #fff;
  grid-column: 3/5;
}

.clear {
  background-color: #f44336;
  color: #fff;
}

.backspace {
  background-color: #2196f3;
  color: #fff;
}

button:active {
  transform: scale(0.95);
}

@media screen and (max-width: 600px) {
  .calculator {
    max-width: 100%;
    padding: 10px;
  }
  
  .buttons {
    grid-template-columns: repeat(3, 1fr);
  }
  
  .equals {
    grid-column: 2/4;
  }
}
</style>
