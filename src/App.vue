<script setup>
import { ref } from "vue";

const nome = ref("");
const idade = ref(null);
const email = ref("");
const mostrarMensagem = ref(false);

function enviarFormulario() {
  if (validarFormulario()) {
    mostrarMensagem.value = true;
  }
}
function validarFormulario() {
  if (nome.value.length < 3 || nome.value.length > 20) {
    alert("O nome deve ter entre 3 e 20 caracteres.");
    return false;
  }
  if (idade.value < 18 || idade.value > 60) {
    alert("A idade deve estar entre 18 e 60 anos.");
    return false;
  }
  if (!email.value.includes("@")) {
    alert("O e-mail deve ser válido.");
    return false;
  }
  return true;
}
</script>

<template>
  <div>
    <label for="nome">Nome:</label>
    <input type="text" id="nome" v-model.lazy="nome" />
    <label for="idade">Idade:</label>
    <input type="number" id="idade" v-model.number.lazy="idade" />
    <label for="email">E-mail:</label>
    <input type="email" id="email" v-model.lazy="email" />
    <button @click="enviarFormulario">Enviar</button>
    <p v-if="mostrarMensagem">Dados enviados com sucesso:</p>
    <ul v-if="mostrarMensagem">
      <li>Nome: {{ nome }}</li>
      <li>Idade: {{ idade }}</li>
      <li>E-mail: {{ email }}</li>
    </ul>
  </div>
</template> 
<style scoped>
.container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
}
label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}
input {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
button {
  background-color: #007bff;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.success-message {
  color: green;
  font-weight: bold;
}
ul {
  list-style-type: none;
  padding: 0;
}
ul li {
  margin-bottom: 5px;
}
.hide {
  display: none;
}
</style>