<template>
  <div class="container" id="home">
    <div class="inicio">
      <div class="inicio-text">
        <h1>LogoName</h1>
        <p>Advocacia</p>
        <span>Contratos de lotação, de distribuição e de franquias Direito Empresarial e Direito Trabalhista</span>
      </div>
    </div>
    <div class="cards">
      <div class="card">
        <h1>Direito Empresarial</h1>
        <span>
          Consultoria e litígios corporativos, incluindo contratos, fusões e aquisições, e disputas comerciais.
        </span>
      </div>
      <div class="card">
        <h1>Direito de Família</h1>
        <span> Atuação em divórcios, guarda de filhos, pensões alimentícias e inventários, priorizando soluções amigáveis.</span>
      </div>
      <div class="card">
        <h1>Direito Penal</h1>
        <span>Defesa em casos criminais, abrangendo crimes financeiros, delitos tecnológicos e crimes contra a pessoa.</span>
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
    document.querySelectorAll('.inicio').forEach(inicio => {
      observer.observe(inicio);
    });
  }
  
}
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  color: #333;
}

.container {
  display: flex;
  flex-direction: column;
  height: auto;
  background: url('/public/IMG/Brown.png');
  background-size: cover;
  padding: 10px;
}

.inicio {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: flex-start;
  text-align: center;
  margin: 0;
  opacity: 0;
  transform: translateY(-50px);
  transition: opacity 0.5s ease-out, transform 0.5s ease-out;
  margin-top:5rem;
}
.inicio.show {
  opacity: 1;
  transform: translateY(0);
}

.inicio-text {
  margin-top: 7.5rem;
  width: 40%;
}

.inicio-text h1 {
  font-size: 2.5rem;
  color: #d8d8d8;
  letter-spacing: 3px;
  font-weight: 900;
}

.inicio-text p {
  color: #979797;
  letter-spacing: 5px;
  font-weight: 500;
}

.inicio-text span {
  width: 10rem;
  text-align: center;
  letter-spacing: 2px;
}

.cards {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 12rem;
  flex-wrap: wrap;
}

.card {
  display: flex;
  align-items: center;
  flex-direction: column;
  text-align: center;
  width: 14rem;
  height: 10rem;
  background: #fffbff;
  border-radius: 10px;
  box-shadow: rgba(0, 0, 0, 0.4) 0px 2px 4px, rgba(0, 0, 0, 0.3) 0px 7px 13px -3px, rgba(0, 0, 0, 0.2) 0px -3px 0px inset;
  margin: 10px;
  opacity: 0;
  transform: translateY(-20px);
  transition: opacity 0.5s ease-out, transform .5s ease-out;
}

.card.show {
  opacity: 1;
  transform: translateY(0);
}

.card h1 {
  margin-top: .5rem;
  font-size: 1rem;
  color: black;
}

.card span {
  font-size: .9rem;
  margin-top: 1rem;
  font-weight: 500;
  color: black;
  margin: 10px;
}

/* Dispositivos pequenos (celulares em modo retrato e menores) */
@media (max-width: 600px) {
  .container{
  background: url('/public/IMG/ab.png');
    
  }
  .cards {
    flex-direction: column;
  }
  .inicio {
    display: flex;
    width: 100%;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .inicio-text {
    margin-top: 5rem;
    width: 70%;
  }
}

/* Dispositivos médios (celulares em modo paisagem e tablets em modo retrato) */
@media (min-width: 601px) and (max-width: 768px) {
  .container{
  background: url('/public/IMG/aa.png');
    
  }
  .cards {
    flex-direction: column;
  }
  .inicio {
    display: flex;
    width: 100%;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .inicio-text {
    margin-top: 5rem;
    width: 70%;
  }
}

/* Dispositivos médios a grandes (tablets em modo paisagem e pequenos desktops) */
@media (min-width: 769px) and (max-width: 1024px) {
  .inicio-text {
    width: 60%;
  }
}

/* Dispositivos grandes (laptops e desktops) */
@media (min-width: 1025px) and (max-width: 1200px) {
  .inicio-text {
    width: 50%;
  }
}

/* Dispositivos extragrandes (desktops grandes) */
@media (min-width: 1201px) {
  .inicio-text {
    width: 40%;
  }
}
</style>
