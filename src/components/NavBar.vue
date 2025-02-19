<template>
  <header :class="{ hidden: hidden }" class="navbar">
    <div class="t">
      <img src="../assets/logocente.png" alt="" class="logo">
      <nav>
        <ul v-if="!isMobile">
          <li @click="handleClick('#home')">Home</li>
          <li @click="handleClick('#sobrenos')">Sobre nós</li>
          <li @click="handleClick('#atuacao')">Áreas de Atuação</li>
          <li @click="handleClick('#artigos')">Artigos</li>
          <li @click="handleClick('#contatos')">Contatos</li>
          <li @click="handleClick('#local')">local</li>
        </ul>
        <v-icon @click.stop="toggleDrawer" v-if="isMobile" style="cursor: pointer;color:black; margin-right:10px;" icon="mdi-menu" />
      </nav>
    </div>
    <v-navigation-drawer v-model="drawer" location="right" class="menuH" temporary>
      <v-card class="headerMenu">
        <v-container class="test">
          <div class="Hnav">         
            <ul class="header-nav">
              <li @click="handleClick('#home')">Home</li>
              <li @click="handleClick('#sobrenos')">Sobre nós</li>
              <li @click="handleClick('#atuacao')">Áreas de Atuação</li>
              <li @click="handleClick('#artigos')">Artigos</li>
              <li @click="handleClick('#contatos')">Contatos</li>
              <li @click="handleClick('#local')">local</li>
            </ul>
            <p>Entrar em contato</p>
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
      <div class="headerAbout-p" v-if="!isMobile">
        <SvgIcon class="icon" type="mdi" :path="mdiLinkedin " />
        <SvgIcon class="icon" type="mdi" :path="mdiInstagram" />
        <p class="duvidas">Dúvidas?</p>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted, onBeforeUnmount, watch } from 'vue'
import SvgIcon from '@jamescoyle/vue-icon'
import {useGoTo} from 'vuetify'

import { mdiPhone, mdiEmailOutline, mdiClockTimeEightOutline, mdiLinkedin, mdiInstagram } from '@mdi/js'

const hidden = ref(false)
let lastScrollTop = 0
const drawer = ref(false)
const isMobile = ref(false)
const goTo = useGoTo()


const toggleDrawer = () => {
  drawer.value = !drawer.value
}

const handleWindowSizeChange = () => {
  isMobile.value = window.innerWidth <= 1030
}
function handleClick(id){
      goTo(id)
    }

const handleScroll = () => {
  const currentScrollTop = window.pageYOffset || document.documentElement.scrollTop
  hidden.value = currentScrollTop > lastScrollTop
  lastScrollTop = currentScrollTop <= 0 ? 0 : currentScrollTop // Para evitar valores negativos
}

onMounted(() => {
  handleWindowSizeChange()
  window.addEventListener('resize', handleWindowSizeChange)
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', handleWindowSizeChange)
})

watch(() => window.innerWidth, () => {
  handleWindowSizeChange()
})
</script>

<style scoped>
.t {
  display: flex;
  align-items: center;
  justify-content: space-between; 
  width: 100%;
}

header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-direction: column;
  width: 100%;
  color: #979797;
  background: #fffbff;
  z-index: 1000;
  transition: top 0.6s ease-in-out;
}
.logo{
  height: 4.5rem;
}
header h1 {
  margin: 10px;
  font-size: 2rem;
}

header nav ul {
  list-style: none;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 10px;
}

header nav ul li {
  margin: 10px;
  font-size: 1rem;
  text-transform: uppercase;
  font-weight: 700;
  letter-spacing: .5px;
  padding: 17px 0;
  cursor: pointer;
  transition: .6s;
}

header nav ul li:hover {
  color: #636363;
}

.headerAbout {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 3.5rem;
  color: #4d4d4d;
  background: #fffbff;
  box-shadow: inset 0px -8px 20px 2px rgb(0 0 0 / 30%);
}

.headerAbout-p {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 10px;
  height: 100%;
}

.headerAbout-p p {
  display: flex;
  align-items: center;
  margin: 10px;
  height: 100%;
  font-size: 1rem;
}

.v-navigation-drawer__scrim{
  height:45rem;

}

.headerMenu {
  display: flex;
  justify-content: center;
  height: 100%;
}

.Hnav {
  display: flex;
  justify-content: space-between;
  height: 100%;
  flex-direction: column;
}

.hidden {
  top: -8rem; /* Ajuste conforme necessário para a altura da sua navbar */
}

.Hnav p { 
  font-size: 1rem;
  background: #d8d8d8;
  letter-spacing: 1px;
  font-weight: 900;
  color: #636363;
  margin: 10px;
  padding: 10px;
  border-radius: 10px;
  text-align: center;
  cursor: pointer;
}

.header-nav {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  list-style: none;
  margin-top: 1rem;
}

.header-nav li {
  font-size: 1rem;
  color: #d8d8d8;
  width: 13rem;
  letter-spacing: 1px;
  font-weight: 900;
  background: #636363;
  margin: 5px;
  padding: 10px;
  border-radius: 10px;
  text-align: center;
  cursor: pointer;
}

.icon {
  cursor: pointer;
}

.duvidas {
  display: flex;
  align-items: center;
  text-align: center;
  height: 4rem;
  background: #65746D;
  color: #ffffff;
  margin: 0px;
  padding: 10px;
  cursor: pointer;
}

/* Dispositivos pequenos (celulares em modo retrato e menores) */
@media (max-width: 600px) {
  .headerAbout-p p {
    display: flex;
    align-items: center;
    margin: 5px;
    height: 100%;
    font-size: .6rem;
  }
}

/* Dispositivos médios (celulares em modo paisagem e tablets em modo retrato) */
@media (min-width: 601px) and (max-width: 768px) {
  .headerAbout-p p {
    display: flex;
    align-items: center;
    margin: 5px;
    height: 100%;
    font-size: .6rem;
  }
}

/* Dispositivos médios a grandes (tablets em modo paisagem e pequenos desktops) */
@media (min-width: 769px) and (max-width: 1024px) {
  .hidden {
  top: -9rem; /* Ajuste conforme necessário para a altura da sua navbar */
}
}

/* Dispositivos grandes (laptops e desktops) */
@media (min-width: 1025px) and (max-width: 1200px) {
  .hidden {
  top: -10rem; /* Ajuste conforme necessário para a altura da sua navbar */
}
}

/* Dispositivos extragrandes (desktops grandes) */
@media (min-width: 1201px) {
  .hidden {
  top: -10.5rem; /* Ajuste conforme necessário para a altura da sua navbar */
}
}
</style>
