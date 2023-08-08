<script setup>
  import { reactive } from 'vue'

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
    return variaveis.num1 !== "" & variaveis.num2 !== "" & variaveis.operacao !== "";
  }


</script>

<template>
  <div class="container mt-5 pb-5">
    <header>
      <div class="row mt-2">
        <h1>Calculadora</h1>
        <h4>Digite os números e selecione a operação desejada</h4>
        <p>(Para resultados fracionados o arredondamento é em até 3 casas decimais)</p>
      </div>
    </header>
    <form>
      <div class="row justify-content-center align-items-center mt-5">
        <div class="col-md-2">
          <input @change="evento => variaveis.num1 = evento.target.value" class="form-control" type="number" placeholder="Num1" required>
        </div>
        <div class="col-md-1">
          <select @change="evento => variaveis.operacao = evento.target.value" class="form-control" >
            <option value=""></option>
            <option value="adicao">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">x</option>
            <option value="divisao">÷</option>
          </select>
        </div>
        <div class="col-md-2">
          <input @change="evento => variaveis.num2 = evento.target.value" class="form-control" type="number" placeholder="Num2" required>
        </div>
        <div class="col-md-1">
          <span>=</span>
        </div>
        <div class="col-md-3">
          <span v-if="camposEstaoPreenchidos()" :variaveis.resultado = realizaOperacao() class="form-control cor-result">{{ variaveis.resultado }}</span>
        </div>
      </div>
    </form>
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

input {
  background-color: rgb(252, 252, 186);
}

select {
  background-color: rgb(253, 183, 183);
}

input, select {
  font-size: 40px;
}

span {
  font-size: 40px;
}

.cor-result {
  background-color: rgb(154, 253, 171);
  color: #0c1077;
}

</style>
