<template>
  <v-app>
    <div v-if="!isLoaded">
      <preloader />
    </div>
    <div v-else>
      <NavBar />
      <v-main>
        <Home />
        <SobreNos />
        <Atuacao />
        <Artigos />
        <Contatos />
        <Local />
        <Foot />
      </v-main>
    </div>
  </v-app>
</template>

<script setup>
import { ref, onMounted } from 'vue';

// Estado para controlar a visibilidade dos componentes
const isLoaded = ref(false);

onMounted(() => {
  document.onreadystatechange = () => {
    if (document.readyState === "complete") {
      setTimeout(() => {
        isLoaded.value = true;
  }, 3000);
         }
  };
});
</script>

