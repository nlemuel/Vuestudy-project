<template>
  <div class="about">
    <h1>Salve {{ nome }}!</h1>

    <div class="inputs">
      <label for="nome">Nome </label>
      <input id="nome" type="text" v-model="nome" />
    </div>
    <div class="inputs">
      <label for="senha">Senha </label>
      <input id="senha" type="password" v-model="senha" />
    </div>  
      
      
      
    
    
    <button @click="cadastrar">Cadastrar</button>
    <p v-if="erro">{{ erro }}</p>
    <div class="input-container">
      <input type="text" v-model="nome" />
    <p class="p" v-if="nome.length > 5 ">Nome grande</p>
    <p class="p" v-else>Nome pequeno</p>

     <div class="table">
      <table>
        <thead>
          <td>Id</td>
          <td>Nome</td>
        </thead>
        <tr v-for="usuario in usuarios" :key="usuario.id">
          <td>{{ usuario.id }}</td>
          <td>{{ usuario.nome }}</td>
        </tr>
      </table>
     </div> 
      
    </div>
    
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';
import axios from 'axios';

const nome = ref("Nome");
const senha = ref("123");
const erro = ref();
const usuarios = ref();

async function atualizar() {
  try {
    usuarios.value = (await axios.get("usuario")).data;
  }
  catch(ex) {
    erro.value = (ex as Error).message;
  }
}

async function cadastrar() {
  try {
    await axios.post("usuario",
  {
    nome: nome.value,
    senha: senha.value
  });
  }
  catch(ex) {
    erro.value = (ex as Error).message;
  }
  
  atualizar();
}

onMounted(() => {
  atualizar();
});
</script>
<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }

  .input-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  
}

.table{
  display: flex;
  justify-content: center;
  align-items: center;

  margin-top: 1rem;
}

.p{
  margin-left: 1rem;
}
.inputs{
  margin-bottom: 1rem;
}
}
</style>
