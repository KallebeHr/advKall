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
        @click="handleClick(link)"
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
      'CONTATOS',
    ],
  }),
  methods: {
    handleClick(link) {
      const sections = {
        'Home': '#home',
        'SOBRE NÓS': '#sobrenos',
        'ÁREAS DE ATUAÇÃO': '#atuacao',
        'ARTIGOS': '#artigos',
        'CONTATOS': '#contatos',
      };
      const target = sections[link];
      const element = document.querySelector(target);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
    },
  },
};
</script>

<style scoped>
.footer {
  background: black;
  color: white;
}
</style>
