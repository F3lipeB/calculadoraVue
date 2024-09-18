<script setup>
  import { reactive} from 'vue';

  const estado = reactive({
    valor1: '',
    valor2: '',
    calculos: {
      divi: (a, b) => a / b, 
      mult: (a, b) => a * b,
      soma: (a, b) => a + b,
      subt: (a, b) => a - b,
    },
    resultado: '',
  })

  const resultado = () => {
    const { valor1, valor2, calculo } = estado;
    estado.resultado = estado.calculos[calculo](parseFloat(valor1), parseFloat(valor2))
  }

</script>

<template>
  <div class="container">
    <h1>Calculadora Aritmética</h1>
    <div class="form">
      <input type="text" v-model="estado.valor1" @input="resultado" />
      <input type="text" v-model="estado.valor2" @input="resultado" />
      <select v-model="estado.calculo" @change="resultado">
        <option value="divi">Divisão</option>
        <option value="mult">Multiplicação</option>
        <option value="soma">Soma</option>
        <option value="subt">Subtração</option>
      </select>
      <p>{{ estado.resultado }}</p>
    </div>
  </div>
</template>

<style scoped>
  input {
    margin: 8px 4px;
    padding: 8px;
    width: 180px;
    align-items: center;
    text-align: center;
  }

  select {
    margin: 0 4px;
    padding: 8px;
    width: 368px;
    color: rgb(58, 216, 155);
    background-color: rgb(145, 148, 145);
    border: 2px solid;
    align-items: center;
    text-align: center;
  }

  option {
    font-size: 24px;
    text-align: center
  }

  p {
    margin: 16px 4px;
    padding: 8px;
    width: 368px;
    border: 1px solid;
    align-items: center;
    text-align: center;
  }
</style>