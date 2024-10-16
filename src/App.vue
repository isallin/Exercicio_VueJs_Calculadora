<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    valor1:0,
    valor2:0,
    resultado:0,
    filtro: '',
  })

  function alteraValor1(evento) {
    estado.valor1 = Number(evento.target.value);
  }

  function alteraValor2(evento) {
    estado.valor2 = Number(evento.target.value);
  }

  function operacao(){
    if (estado.filtro === 'adicao') {
      return estado.valor1 + estado.valor2;
    } else if (estado.filtro === 'subtracao') {
      return estado.valor1 - estado.valor2;
    } else if (estado.filtro === 'multiplicacao') {
      return estado.valor1 * estado.valor2;
    } else if (estado.filtro === 'divisao')  {
      return estado.valor1 / estado.valor2;
    } else {
      return 'Resultado'
    }
  }

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-success rounded-3 text-white">
      <h1 class="display-1">Calculadora aritmética</h1>
      <h5>Insira os valores e escolha a operação que deseja calcular</h5>
    </header>

    <form>
      <div class="row">
        <div class="col">
          <input type="number" placeholder="Insira um valor" class="form-control p-3" @keyup="alteraValor1">
        </div>
        <div class="col">
          <input type="number" placeholder="Insira outro valor" class="form-control p-3" @keyup="alteraValor2">
        </div>
        <div class="col">
          <select class="form-control p-3 bg-success text-white" @change="evento => estado.filtro = evento.target.value">
            <option>Selecione a operação</option>
            <option value="adicao">Adição</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
      </div>
      <span>
        <p class="mt-5 p-3 bg-success text-white rounded-3">
          {{operacao()}}
        </p>
      </span>
    </form>
  </div>
</template>

<style scoped>
.container{
  text-align: center;
}

p{
  font-size: 5em;
}
</style>
