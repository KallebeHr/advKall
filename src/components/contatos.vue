<template>
    <div class="container">
      <div class="card">
        <h1>Estamos disponíveis para ajudar.</h1>
  
        <div class="inputsP">
          <div class="inputsT">
            <v-text-field class="name" label="Nome"></v-text-field>
            <v-text-field class="tell" label="Celular"></v-text-field>
          
          </div>
          <div class="inputsT">
            <v-select
  label="Ajuda com"
  class="help"
  :items="['Direito Civil', 'Direito Empresarial', 'Direito de Família', 'Direito Sucessório']"
></v-select>
            <v-text-field class="email" label="Email"></v-text-field>
          </div>
        </div>
        <v-textarea
        class="message"
      label="Mensagem"
      counter
    ></v-textarea>
  
        <v-btn class="submit-btn" color="primary">Enviar</v-btn>
      </div>
    </div>
  </template>
  
  <script>
  export default {
 
  
  }
  </script>
  
  <style scoped>
  .container {
    display: flex;
    justify-content: center;
    height: auto;
    width: 100%;
    background: #fffbff;
    color: black;
    padding: 2rem;
  }
  
  .card {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: auto;

    align-items: center;
    width: 100%;
    max-width: 600px;
    background: white;
    padding: 2rem;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }
  .card h1{
    text-align: center;
  }
  .inputsP {
    display: flex;
    justify-content: center;
    align-items: center;
    height: auto;

    width: 100%;
    margin-bottom: 1rem;
  }
  
  .inputsT {
    display: flex;
    flex-direction: column;
    color:black;
    margin:10px;
    height: auto;
    width:auto;

  }
 .name, .tell, .help, .email{
  margin:10px;
  width: 15rem;
  height: 3rem;
 } 
 .message{
  margin:10px;
  width: 97%;
  height: 4rem;
 }
  .submit-btn {
    margin-top: 6rem;
  }
  /* Dispositivos pequenos (celulares em modo retrato e menores) */
@media (max-width: 600px) {
  .inputsP {
    flex-direction: column;
  }
}

/* Dispositivos médios (celulares em modo paisagem e tablets em modo retrato) */
@media (min-width: 601px) and (max-width: 768px) {
  .inputsP {
    flex-direction: column;
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
  