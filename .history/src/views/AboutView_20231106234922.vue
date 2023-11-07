<template>
  <div class="about">
    <h1>Salve {{ nome }}!</h1>
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
import { ref } from 'vue';

const nome = ref("Nome");
const usuarios = ref([
  { id: 1, nome: "usuario 1", senha: "123" },
  { id: 2, nome: "usuario 2", senha: "456"}
]);
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
  
}

.p{
  margin-left: 1rem;
}
}
</style>
