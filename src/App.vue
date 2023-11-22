<script setup>
import { reactive } from 'vue';

    const estado = reactive({
        filtro: '',

        valorDoCampo1: 0,
        valorDoCampo2: 0
    })

    function soma(a,b) {
        return parseInt(a) + parseInt(b)
    }

    function subtracao(a,b) {
        return a - b
    }

    function multiplicacao(a,b) {
        return a * b
    }

    function divisao(a,b) {
        return a / b
    }

    const operacao = () => {
    const { valorDoCampo1,valorDoCampo2,filtro } = estado;
        
    switch (filtro) {
        case 'Soma':
            return soma(valorDoCampo1,valorDoCampo2);
        case 'Subtração':
            return subtracao(valorDoCampo1,valorDoCampo2);
        case 'Multiplicação':
            return multiplicacao(valorDoCampo1,valorDoCampo2);
        case 'Divisão':
            return divisao(valorDoCampo1,valorDoCampo2);
        default:
            return soma(valorDoCampo1,valorDoCampo2);
    }
}

</script>

<template>
    <body>
        <div class="container text-center">
            <h1 class="fs-1">Calculadora Aritmética</h1>
            <h3 class="fs-6">Insira os números nos campos abaixo e escolha a operação que deseja realizar</h3>
            <div class="form">
                <input required @keyup="event => estado.valorDoCampo1 = event.target.value" type="number" class="form-control" placeholder="Digite o número">
                <input required @keyup="event => estado.valorDoCampo2 = event.target.value" type="number" class="form-control" placeholder="Digite o número">
                <br>
                <select @change="evento => estado.filtro = evento.target.value">
                    <option selected>Soma</option>
                    <option>Subtração</option>
                    <option>Multiplicação</option>
                    <option>Divisão</option>
                </select>
                <p>{{ operacao() }}</p>
            </div>
        </div>
    </body>
</template>

<style scoped>
</style>
