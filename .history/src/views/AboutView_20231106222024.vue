<template>
  <div class="about">
    <h1>Bem-vindo {{ nome }}!</h1>
    <div>
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
    min-height: 100vh;
    display: inline-block;
    align-items: center;
  }
}
</style>
