<template>
  <div class="about">
    <h1>Bem-vindo {{ nome }}!</h1>
    <div class="input-container">
      <input type="text" v-model="nome" />
    <p v-if="nome.length > 5 ">Nome grande</p>
    <p v-else>Nome pequeno</p>
    </div>
    
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const nome = ref("Nome");
</script>
<style>
@media (min-width: 1024px) {
  .about {
    border: solid 1px;
    min-height: 100vh;
    display: flex;
    align-items: center;
    flex-direction: column;

    border: solid 1px;
  }

  .input-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 20%;

  border: solid 1px;
}
}
</style>
