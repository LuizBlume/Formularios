<script>
import { ref } from "vue";

export default {
  setup() {
    const dados = ref({
      nome: "",
      idade: null,
      email: "",
    });
    const mostrarMensagem = ref(false);

    function enviarFormulario() {
      mostrarMensagem.value = true;
    }

    return {
      dados,
      mostrarMensagem,
      enviarFormulario,
    };
  },
};
</script>

<template>
  <div>
    <label for="nome">Nome:</label>
    <input type="text" id="nome" v-model="nome" />
    <label for="idade">Idade:</label>
    <input type="number" id="idade" v-model="idade" />
    <label for="email">E-mail:</label>
    <input type="email" id="email" v-model="email" />
    <button @click="enviarFormulario">Enviar</button>
    <p v-if="mostrarMensagem">Dados enviados com sucesso:</p>
    <ul v-if="mostrarMensagem">
      <li>Nome: {{ nome }}</li>
      <li>Idade: {{ idade }}</li>
      <li>E-mail: {{ email }}</li>
    </ul>
  </div>
</template> 