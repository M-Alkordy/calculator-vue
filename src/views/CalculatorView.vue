<template>
  <div class="Calculator">
    <div class="screen">
      <p>
        {{ previous_operation }} <br />
        {{ process }} <br />
        =
        {{ result }}
      </p>
    </div>
    <div class="btns">
      <button @click="deleteProcess()">AC</button>
      <button @click="DeleteLastItem()">DEL</button>
      <button @click="showOnScreen('%')">%</button>
      <button @click="showOnScreen('/')">/</button>
      <button @click="showOnScreen(7)">7</button>
      <button @click="showOnScreen(8)">8</button>
      <button @click="showOnScreen(9)">9</button>
      <button @click="showOnScreen('*')">X</button>
      <button @click="showOnScreen(4)">4</button>
      <button @click="showOnScreen(5)">5</button>
      <button @click="showOnScreen(6)">6</button>
      <button @click="showOnScreen('-')">ــ</button>
      <button @click="showOnScreen(1)">1</button>
      <button @click="showOnScreen(2)">2</button>
      <button @click="showOnScreen(3)">3</button>
      <button @click="showOnScreen('+')">+</button>
      <button @click="showOnScreen('00')">00</button>
      <button @click="showOnScreen(0)">0</button>
      <button @click="showOnScreen('.')">,</button>
      <button @click="showResult()">=</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "CalculatorView",
  data() {
    return {
      previous_operation: "",
      process: "",
      result: "",
    };
  },
  methods: {
    showOnScreen(value) {
      if (this.result) {
        this.result += String(value);
        this.process = "";
      } else {
        this.process += value;
      }
    },
    deleteProcess() {
      this.process = "";
      this.previous_operation = "";
      this.result = "";
    },
    DeleteLastItem() {
      this.process = this.process.slice(0, -1);
    },
    showResult() {
      if (!this.process) {
        this.process = this.result;
      }
      if (this.result) {
        this.result = eval(this.result);
      } else {
        this.result = eval(this.process);
      }
      this.previous_operation = String(this.process + "=" + this.result);
    },
  },
};
</script>

<style>
.Calculator {
  width: 344px;
  border: 2px solid #1e3a8a;
  border-radius: 6px;
  background-color: #0f172a;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.screen {
  width: 314px;
  height: 250px;
  border-radius: 6px;
  margin-bottom: 8px;
  margin-top: 44px;
  background-color: #1e293b;
  position: relative;
  left: 50%;
  transform: translatex(-50%);
  font-size: 48px;
  color: white;
  text-align: right;
}
.btns {
  width: 92%;
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  position: relative;
  left: 50%;
  transform: translatex(-50%);
  margin-bottom: 8px;
}
button {
  width: 72px;
  height: 60px;
  border: none;
  border-radius: 6px;
  background-color: #1e293b;
  cursor: pointer;
  font-size: 30px;
  color: white;
}
</style>
