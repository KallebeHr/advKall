<template>
    <v-footer class="footer">
      <v-row justify="center" no-gutters>
        <v-btn
          v-for="link in links"
          :key="link"
          class="mx-2"
          color="white"
          rounded="xl"
          variant="text"
        >
          {{ link }}
        </v-btn>
        <v-col class="text-center mt-4" color="white" cols="12">
          {{ new Date().getFullYear() }} — <strong>Kallebe</strong>
        </v-col>
      </v-row>
    </v-footer>
  </template>
  <script>
    export default {
      data: () => ({
        links: [
          'Home',
          'SOBRE NÓS',
          'ÁREAS DE ATUAÇÃO',
          'ARTIGOS',
          'EQUIPE',
          'CONTATOS',
        ],
      }),
    }
  </script>

  <style scoped>
  .footer{
    background:black;
    color:white;
  }
  </style>