<script setup>
  import { reactive } from 'vue'
  import Cabecalho from './components/Cabecalho.vue'
  import Formulario from './components/Formulario.vue'
  
  const variaveis = reactive({
    num1: 0,
    num2: 0,
    resultado: 0,
    operacao: ''
  })

  const realizaOperacao = () => {

    const { operacao } = variaveis;
    
    switch(operacao) {
      case 'adicao': 
        return soma();
      case 'subtracao':
        return subtrai();
      case 'multiplicacao': 
        return multiplica();
      case 'divisao':
        return divide();
      default:
        return 0;
    }

  }
  
  const soma = () => {
    variaveis.resultado = retiraZerosAposVirgula((parseFloat(variaveis.num1) + parseFloat(variaveis.num2)).toFixed(3))
    return variaveis.resultado
  }

  const subtrai = () => {
    variaveis.resultado = retiraZerosAposVirgula((variaveis.num1 - variaveis.num2).toFixed(3))
    return variaveis.resultados
  }

  const multiplica = () => {
    variaveis.resultado = retiraZerosAposVirgula((variaveis.num1 * variaveis.num2).toFixed(3))
    return variaveis.resultado
  }

  const divide = () => {
    if(variaveis.num1 % variaveis.num2 == 0) {
      variaveis.resultado = (variaveis.num1 / variaveis.num2)
    }
    else {
      variaveis.resultado = retiraZerosAposVirgula((variaveis.num1 / variaveis.num2).toFixed(3))
    }
  
    return variaveis.resultado
  }

  function retiraZerosAposVirgula(str) {
    return parseFloat(str)
    .toString()
    .replace('.', ',');
  }

  const camposEstaoPreenchidos = () => {
    return variaveis.num1 != "" && variaveis.num2 != "" && variaveis.operacao != "";
  }
</script>

<template>
  <div class="container mt-5 pb-5">
    <Cabecalho />
    <Formulario :edita-num1="evento => variaveis.num1 = evento.target.value" :edita-operacao="evento => variaveis.operacao = evento.target.value"
      :edita-num2="evento => variaveis.num2 = evento.target.value" :campos-preenchidos="camposEstaoPreenchidos()" :resultado="variaveis.resultado" :realizaOperacao="realizaOperacao()" />
  </div>
</template>

<style scoped>
* {
  text-align: center;
  color: #48dbfb;
}

.container {
  background-color: #222f3e;
}
</style>
