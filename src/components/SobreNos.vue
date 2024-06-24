<template>
  <div class="container" id="sobrenos">
    <div class="container-text">
      <div class="titulo">
        <h1 class="titulo-h1">Princípios</h1>
        <div class="linha">.</div>
      </div>
      <div class="texto">
        <p class="text-p">Pautamos nossas atividades pela ética e lealdade. Cientes de que a diversidade e a equidade são indispensáveis para a longevidade saudável da sociedade, respeitamos e valorizamos as posições e princípios morais de todos. Primamos pelo exercício reto e probo da Advocacia, com competência profissional, eficiência, agilidade e polidez no trato com nossos clientes e parceiros.

Nosso objetivo é ser referência no atendimento a empreendedores, seja no consultivo, seja no contencioso. Oferecemos aos clientes um serviço de excelência, antecipando as suas necessidades e buscando suprir todas as suas expectativas.</p>
      </div>
    </div>
    <div class="cards">
      <div class="card">
        <img src="/public/IMG/adv1.png" alt="">
        <h1>MAIS DE 25 ANOS</h1>
        <span>
          Referência em Direito Empresarial para o mercado varejista, de franquias e postos de combustíveis. Atua em consultoria estratégica dentro de suas áreas de especialização com a intenção de prevenir contendas judiciais e na elaboração de estudos e pareceres jurídicos. 
        </span>
      </div>
      <div class="card">
        <img src="/public/IMG/adv2.png" alt="">

        <h1>FORTE ATUAÇÃO</h1>
        <span>É reconhecido pela forte atuação no setor varejista, atendendo seus clientes seja na fase pré-negocial, quanto na formalização de seus contratos de locação comercial, sendo especializado em questões que envolvem shoppings, franquias e revenda de combustíveis.</span>
      </div>
      <div class="card">
        <img src="/public/IMG/adv3.png" alt="">
        <h1>CONTRATOS</h1>
        <span>Larga experiência em contratos de locação comercial, contratos de franquia, ações revisionais de aluguel, renovatórias de contrato, despejo e relações jurídicas contratuais de postos de combustíveis.</span>
      </div>
      <div class="card">
        <img src="/public/IMG/adv4.png" alt="">
        <h1>FRANQUIA</h1>
        <span>Assessoria jurídica completa para franqueador e o franqueado, desde o estudo da proposta do contrato de franquia até distrato, passando pela elaboração da Circular de Oferta de Franquia (COF).</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
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

    document.querySelectorAll('.card').forEach(card => {
      observer.observe(card);
    });
    document.querySelectorAll('.titulo-h1').forEach(h1 => {
      observer.observe(h1);
    });
    document.querySelectorAll('.linha').forEach(linha => {
      observer.observe(linha);
    });
    document.querySelectorAll('.text-p').forEach(p => {
      observer.observe(p);
    });

  }
}
</script>

<style scoped>
.container{
    display:flex;
    justify-content: center;
    height: auto;
    background: #fffbff;

    color:black;
    flex-direction: column;
}
.cards {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 5rem;
  flex-wrap: wrap;
}

.card {
  display: flex;
  align-items: center;
  flex-direction: column;
  text-align: center;
  width: 17rem;
  height: 30rem;
  background: #070000;
  border-radius: 10px;
  box-shadow: rgba(0, 0, 0, 0.4) 0px 2px 4px, rgba(0, 0, 0, 0.3) 0px 7px 13px -3px, rgba(0, 0, 0, 0.2) 0px -3px 0px inset;
  margin: 10px;
  margin-bottom: 5rem;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.5s ease-out, transform 5s ease-out;
  color: #6D6D6D;
}
.card.show {
  opacity: 1;
  transform: translateY(0);
}
.card img{
  margin-top:2rem;
}
.card h1 {
  margin-top: 2rem;
  font-size: 1rem;
  color: white;
  }

.card span {
  font-size: 1rem;
  margin-top: 1rem;
  font-weight: 700;
  margin: 10px;
  letter-spacing: 1px;
}
.container-text{
    display:flex;
    justify-content: space-around;
    width: 100%;
    margin-top:5rem;

}
.texto{
  display:flex;
  justify-content: center;
  color:#6D6D6D;
  line-height: 1.7;
  width:40%;
  font-size: 1.1rem;
  font-weight: 600;
  letter-spacing: 1px;
}
.texto .text-p{
    opacity: 0;
    transform: translateX(20px);
    transition: opacity 0.5s ease-out, transform .5s ease-out;
  margin:10px;
  text-align: center;

}
.text-p.show{
  opacity: 1;
  transform: translateX(0);
}
.titulo .titulo-h1{
  font-size: 24px;
    font-weight: 700;
    letter-spacing: 0px;
    text-transform: none;
    color: #2c2c2c;
    opacity: 0;
    transform: translateX(-20px);
    transition: opacity 0.5s ease-out, transform .5s ease-out;

}
.titulo-h1.show{
   opacity: 1;
  transform: translateX(0);
}
.linha{
  border-color: #b1976b;
   background: #b1976b;
    width: 5rem;
    height: .6rem;
    border-radius:20px;
    opacity: 0;
    transform: translateX(-20px);
    transition: opacity 0.5s ease-out, transform .5s ease-out;
}
.linha.show{
  opacity: 1;
  transform: translateX(0);
}
/* Dispositivos pequenos (celulares em modo retrato e menores) */
@media (max-width: 600px) {
  .container-text{
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .texto{
    width:90%
  }
}

/* Dispositivos médios (celulares em modo paisagem e tablets em modo retrato) */
@media (min-width: 601px) and (max-width: 768px) {
  .container-text{
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .texto{
    width:70%
  }
}


/* Dispositivos médios a grandes (tablets em modo paisagem e pequenos desktops) */
@media (min-width: 769px) and (max-width: 1024px) {
  .texto{
    width:40%
  }
}

/* Dispositivos grandes (laptops e desktops) */
@media (min-width: 1025px) and (max-width: 1200px) {
  .texto{
    width:40%
  }
}

/* Dispositivos extragrandes (desktops grandes) */
@media (min-width: 1201px) {
  .texto{
    width:40%
  }
}
</style>