<script setup>
import { reactive } from 'vue';

const estado = reactive({
  operacao: 'adicao',
  primeiroNumero: 0,
  segundoNumero: 0,
  resultado: '',
})

function getResultado() {
  estado.resultado = calculadora().toLocaleString('pt-BR');
}

function calculadora(){
  const { operacao } = estado;
  if (Number(estado.segundoNumero)==0 & operacao=='divisao') {
    alert('Divisão por Zero!');
    return;
  }
  switch (operacao) 
  {
    case 'adicao':
      return Number(estado.primeiroNumero) + Number(estado.segundoNumero);
    case 'subtracao':
      return Number(estado.primeiroNumero) - Number(estado.segundoNumero);
    case 'multiplicacao':
      return Number(estado.primeiroNumero) * Number(estado.segundoNumero);
    case 'divisao':
      return Number(estado.primeiroNumero) / Number(estado.segundoNumero);
  }
}

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 bg-light rounded-4 text-center">
      <h1>Calculadora Aritmética</h1>
    </header>
    <form @change="getResultado()">
      <div class="row">
        <div class="col">
            <label for="n1">1º Número:</label>
            <input @change="evento => estado.primeiroNumero = evento.target.value" type="text" id="n1" class="form-control">
        </div>
        <div class="col">
          <label for="n2">2º Número:</label>
            <input @change="evento => estado.segundoNumero = evento.target.value" type="text" id="n2" class="form-control">
        </div>
        <div class="col-md-1">
            <label for="oper">Operação:</label>
            <select @change="evento => estado.operacao = evento.target.value" class="form-control" id="oper">
              <option value="adicao">+</option>
              <option value="subtracao">-</option>
              <option value="multiplicacao">*</option>
              <option value="divisao">/</option>
            </select>
        </div>
        <div class="col">
          <label for="n3">Resultado:</label>
            <input @change="evento => estado.segundoNumero = evento.target.value" type="text" id="n3" class="form-control bg-info" :value=estado.resultado>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>

</style>
