<template>
  <div class="calculator">
    <input type="number" v-model="number1" @input="calculate" placeholder="Número 1">
    <input type="number" v-model="number2" @input="calculate" placeholder="Número 2">
    <select v-model="operation" @change="calculate">
      <option value="+">Soma (+)</option>
      <option value="-">Subtração (-)</option>
      <option value="*">Multiplicação (*)</option>
      <option value="/">Divisão (/)</option>
    </select>
    <div class="result">Resultado: {{ result }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      number1: 0,
      number2: 0,
      operation: '+',
      result: 0
    };
  },
  methods: {
    calculate() {
      const num1 = parseFloat(this.number1);
      const num2 = parseFloat(this.number2);

      switch (this.operation) {
        case '+':
          this.result = num1 + num2;
          break;
        case '-':
          this.result = num1 - num2;
          break;
        case '*':
          this.result = num1 * num2;
          break;
        case '/':
          this.result = num2 !== 0 ? num1 / num2 : 'Erro: Divisão por zero';
          break;
        default:
          this.result = 0;
          break;
      }
    }
  }
};
</script>

<style scoped>
.calculator {
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background: #fff;
  padding: 20px;
  width: 300px;
  margin: 0 auto;
}
.calculator input, .calculator select {
  width: 100%;
  margin-bottom: 10px;
  padding: 10px;
  font-size: 16px;
}
.result {
  font-size: 20px;
  font-weight: bold;
}
</style>
