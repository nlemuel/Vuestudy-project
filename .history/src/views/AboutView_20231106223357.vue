<template>
  <div class="about">
    <h1>Salve {{ nome }}!</h1>
    <div class="input-container">
      <input type="text" v-model="nome" />
    <p class="p" v-if="nome.length > 5 ">Nome grande</p>
    <p class="p" v-else>Nome pequeno</p>
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
