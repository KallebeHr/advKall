<template>
  <header>
    <h1>LogoName</h1>
    <nav>
      <ul v-if="!isMobile">
        <li>Home</li>
        <li>Sobre nós</li>
        <li>Áreas de Atuação</li>
        <li>Artigos</li>
        <li>Equipe</li>
        <li>Contato</li>
        
      </ul>
      <v-icon @click.stop="toggleDrawer" v-if="isMobile" style="cursor: pointer;color:black; margin-right:10px;"
          icon="mdi-menu" />
    </nav>
  </header>
  <v-navigation-drawer v-model="drawer" location="right" temporary class="menuH">
    <v-card class="headerMenu">
      <title>Menu</title>
      <v-container class="test">
        <div>
          <v-btn class="bnt-menu" outlined>
             Rifas
          </v-btn>
          <v-btn class="bnt-menu">
             Times e Apostas
          </v-btn>
          <v-btn class="bnt-menu">
             Apostas Ativas
          </v-btn>

        </div>
      </v-container>
    </v-card>
  </v-navigation-drawer>
  <div class="headerAbout">
    <div class="headerAbout-p">
      <p>
        <SvgIcon type="mdi" :path="mdiPhone" /> 86 9 8163-2626
      </p>
      <p>
        <SvgIcon type="mdi" :path="mdiEmailOutline " /> Kalebeheuler@gmail.com
      </p>
      <p>
        <SvgIcon type="mdi" :path="mdiClockTimeEightOutline " /> Seg - Sex 8h30-18h00
      </p>
    </div>
    <div class="headerAbout-p"  v-if="!isMobile">
      <SvgIcon class="icon" type="mdi" :path="mdiLinkedin " />
      <SvgIcon class="icon" type="mdi" :path="mdiInstagram" />
      <p class="duvidas">Dúvidas?</p>
    </div>
  </div>
</template>
  
  <script setup> 
  import { ref } from 'vue';
  import SvgIcon from '@jamescoyle/vue-icon';
  import { mdiClover,mdiPhone,mdiEmailOutline,mdiClockTimeEightOutline,mdiLinkedin,mdiInstagram  } from '@mdi/js';
   
  
  const path = ref()
  const isMobile = ref(false);
  const drawer = ref(false);
  const toggleDrawer = () => {
  drawer.value = !drawer.value;
};
const handleWindowSizeChange = () => {
  isMobile.value = window.innerWidth <= 1030;
};

onMounted(() => {
  handleWindowSizeChange();
  window.addEventListener('resize', handleWindowSizeChange);
});

onBeforeUnmount(() => {
  window.removeEventListener('resize', handleWindowSizeChange);
});

watch(() => window.innerWidth, () => {
  handleWindowSizeChange();
});

  </script>
  
  <style scoped>
  header{
      display:flex;
      align-items: center;
      justify-content: space-between;
      width: 100%;
      height: 6rem;
      color:#979797;
      background: #fffbff;
      padding:10px;
  }
  header h1{
      margin:10px;
      font-size: 2rem;
  }
  header nav ul {
      list-style: none;
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin:10px;
  
  }
  header nav ul li{
      margin:10px;
      font-size: 1rem;
      text-transform: uppercase;
      font-weight: 700;
      letter-spacing: .5px;
      padding: 17px 0;
      cursor: pointer;
      transition: .6s;
  }
  header nav ul li:hover{
      color:#636363
  }
  .headerAbout{
      display:flex;
      align-items: center;
      justify-content: space-between;
      width: 100%;
      height: 3.5rem;
      color:#4d4d4d;
      background: #fffbff;
      box-shadow: inset 0px -8px 20px 2px rgb(0 0 0 / 30%);
      
    }
    .headerAbout-p{
        display:flex;
        align-items: center;
        justify-content: space-between;
        margin:10px;
        height: 100%;
  
  }
  .headerAbout-p p {
      display:flex;
      align-items: center;
      margin:10px;
      height: 100%;
      font-size:1rem;
  }
  .icon{
      cursor:pointer;
  }
  .duvidas{
      display:flex;
      align-items: center;
      text-align: center;
      height: 4rem;
      background:#65746D;
      color:#ffffff;
      margin:0px;
      padding:10px;
      cursor:pointer;
  }


  /* Dispositivos pequenos (celulares em modo retrato e menores) */
@media (max-width: 600px) {
  .headerAbout-p p {
      display:flex;
      align-items: center;
      margin:5px;
      height: 100%;
      font-size:.6rem;
  }
}

/* Dispositivos médios (celulares em modo paisagem e tablets em modo retrato) */
@media (min-width: 601px) and (max-width: 768px) {
    .headerAbout-p p {
      display:flex;
      align-items: center;
      margin:5px;
      height: 100%;
      font-size:.6rem;
  }
}

/* Dispositivos médios a grandes (tablets em modo paisagem e pequenos desktops) */
@media (min-width: 769px) and (max-width: 1024px) {
}

/* Dispositivos grandes (laptops e desktops) */
@media (min-width: 1025px) and (max-width: 1200px) {
}

/* Dispositivos extragrandes (desktops grandes) */
@media (min-width: 1201px) {
}
  </style>