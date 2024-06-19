<template>
  <div class="container">
    <div class="titulo">
      <SvgIcon class="icon" type="mdi" :path="mdiInstagram" />
      <h1>@Kallebehr</h1>
    </div>
    <div class="carr">
      <swiper
        :modules="modules"
        :slidesPerView="isMobile ? 1.4 : 2.2"
        :centeredSlides="true"
        :navigation="true"
        class="mySwiper"
      >
        <swiper-slide class="card-text" v-for="(slide, index) in slides" :key="index">
          <img :src="slide.img" :alt="slide.title" class="slide-image" />
          <p>{{ slide.title }}</p>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, watch } from 'vue'
import SvgIcon from '@jamescoyle/vue-icon'
import { mdiInstagram } from '@mdi/js'
import { Swiper, SwiperSlide } from 'swiper/vue'

// Import Swiper core and required modules
import { Pagination, Navigation } from 'swiper/modules'

// Import Swiper styles
import 'swiper/css'
import 'swiper/css/pagination'
import 'swiper/css/navigation'

// Defina os slides com imagens e títulos
const slides = ref([
  { img: './IMG/1c.png', title: 'Direito Empresarial' },
  { img: './IMG/1c.png', title: 'Direito de Família' },
  { img: './IMG/1c.png', title: 'Direito Penal' },
  { img: './IMG/1c.png', title: 'ações revisionais' },
  { img: './IMG/1c.png', title: 'pareceres jurídicos.' },
])

const swiperRef = ref(null)

const setSwiperRef = (swiper) => {
  swiperRef.value = swiper
}

const pagination = {
  type: 'fraction',
}

const modules = [Pagination, Navigation]

const isMobile = ref(false)
const handleWindowSizeChange = () => {
  isMobile.value = window.innerWidth <= 600
}

onMounted(() => {
  handleWindowSizeChange()
  window.addEventListener('resize', handleWindowSizeChange)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', handleWindowSizeChange)
})

watch(() => window.innerWidth, () => {
  handleWindowSizeChange()
})
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  height: auto;
  background: #fffbff;
  flex-direction: column;
}
.slide-image {
  width: 15rem;
  height: 15rem;
  border-radius: 10px;
  box-shadow: rgba(0, 0, 0, 0.4) 0px 2px 4px, rgba(0, 0, 0, 0.3) 0px 7px 13px -3px, rgba(0, 0, 0, 0.2) 0px -3px 0px inset;
}
.mySwiper {
  margin-top: 1rem;
  width: 100%;
  height: 30rem;
  color: black;
  margin-bottom: 1rem;
}
.card-text {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.card-text p {
  margin-top: 1rem;
  font-size: 1rem;
  color: #c2c2c2;
  letter-spacing: 5px;
  font-weight: 900;
}
.titulo {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin-top: 4rem;
  color: black;
}
.icon {
  width: 5rem;
  height: 5rem;
  color: #c2c2c2;
}
.titulo h1 {
  font-size: 2.5rem;
  color: #c2c2c2;
  letter-spacing: 5px;
  font-weight: 900;
}
</style>
