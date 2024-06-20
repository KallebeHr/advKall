<template>
  <div class="container">
    <div class="titulo">
      <div class="line1"></div>
      <div class="name"><p>Áreas de atuação</p></div>
      <div class="line2"></div>
    </div>
    <div class="cards">
      <div class="card1 card" v-for="(card, index) in cards" :key="card.id" :class="'card' + (index + 1)">
        <div class="image">
          <img :src="card.image" alt="Imagem da área de atuação" v-if="card.image">
        </div>
        <div class="content">
          <a :href="card.link">
            <span class="title">
              {{ card.title }}
            </span>
          </a>
          <p class="desc">
            {{ card.description }}
          </p>

          <a class="action" :href="card.contactLink">
            ENTRE EM CONTATO
            <span aria-hidden="true">→</span>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cards: [
        {
          id: 1,
          title: "Direito Civil",
          description: "Contratos, responsabilidade civil, direitos do consumidor, indenizações.",
          link: "#",
          contactLink: "#",
          image: "link-para-imagem-civil.jpg"
        },
        {
          id: 2,
          title: "Direito Empresarial",
          description: "Consultoria empresarial, constituição de empresas, fusões e aquisições, recuperação judicial.",
          link: "#",
          contactLink: "#",
          image: "link-para-imagem-empresarial.jpg"
        },
        {
          id: 3,
          title: "Direito de Família",
          description: "Divórcios, guarda e regulamentação de visitas, pensão alimentícia, partilha de bens.",
          link: "#",
          contactLink: "#",
          image: "link-para-imagem-familia.jpg"
        },
        {
          id: 4,
          title: "Direito Sucessório",
          description: "Testamentos, inventários, partilhas, planejamento sucessório.",
          link: "#",
          contactLink: "#",
          image: "link-para-imagem-sucessorio.jpg"
        },
        
      ]
    };
  },
  mounted() {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('show');
        } else {
          entry.target.classList.remove('show');
        }
      });
    });

    document.querySelectorAll('.line1, .line2, .name').forEach(element => {
      observer.observe(element);
    });
    document.querySelectorAll('.card1, .card2, .card3, .card4, .card5').forEach(element => {
      observer.observe(element);
    });
  }
}
</script>

<style scoped>
.container {
  display: flex;
  align-items: center;
  height: auto;
  background: url('/public/IMG/banners.png');
  background-size: cover;
  background-attachment: fixed;
  background-position: center;
  padding: 10px;
  flex-direction: column;
  color: white;
  margin: 10px;
}

.titulo {
  display: flex;
  align-items: center;
  margin-top: 3rem;
  width: 100%;
}

.line1 {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 3px;
  background: white;
  border-radius: 5px;
  width: 100%;
  opacity: 0;
  transform: translateX(-20px);
  transition: opacity 0.5s ease-out, transform 0.5s ease-out;
}
.line2 {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 3px;
  background: white;
  border-radius: 5px;
  width: 100%;
  opacity: 0;
  transform: translateX(20px);
  transition: opacity 0.5s ease-out, transform 0.5s ease-out;
}

.line1.show, .line2.show {
  opacity: 1;
  transform: translateY(0);
}

.name {
  margin: 0 10px;
  font-size: 2rem;
  font-weight: 900;
  white-space: nowrap;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.5s ease-out, transform 0.5s ease-out;
}

.name.show {
  opacity: 1;
  transform: translateY(0);
}

.cards {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  margin-top: 2rem;
}

.card1, .card2 {
  max-width: 300px;
  border-radius: 0.5rem;
  background-color: #fff;
  box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  border: 1px solid transparent;
  margin: 10px;
  opacity: 0;
  transform: translateX(-20px);
  transition: opacity 0.5s ease-out, transform 0.5s ease-out;
}
.card3, .card4 {
  max-width: 300px;
  border-radius: 0.5rem;
  background-color: #fff;
  box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  border: 1px solid transparent;
  margin: 10px;
  opacity: 0;
  transform: translateX(20px);
  transition: opacity 0.5s ease-out, transform 0.5s ease-out;
}
.card1:hover ,.card2:hover,.card3:hover,.card4:hover{
} 
.card1.show, .card2.show, .card3.show, .card4.show  {
  opacity: 1;
  transform: translateY(0);
}
.card1 a, .card2 a, .card3 a, .card4 a {
  text-decoration: none;
}

.content {
  padding: 1.1rem;
}

.image {
  object-fit: cover;
  width: 100%;
  height: 150px;
  background-color: rgb(119, 119, 119);
}

.title {
  color: #111827;
  font-size: 1.125rem;
  line-height: 1.75rem;
  font-weight: 600;
}

.desc {
  margin-top: 0.5rem;
  color: #6B7280;
  font-size: 0.875rem;
  line-height: 1.25rem;
}

.action {
  display: inline-flex;
  margin-top: 1rem;
  color: #ffffff;
  font-size: 0.875rem;
  line-height: 1.25rem;
  font-weight: 500;
  align-items: center;
  gap: 0.25rem;
  background-color: #2563EB;
  padding: 4px 8px;
  border-radius: 4px;
}

.action span {
  transition: 0.3s ease;
}

.action:hover span {
  transform: translateX(4px);
}
</style>
