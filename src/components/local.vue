<template>
  <div class="container" id="local">
    
    <div class="local">
      
        <h1>Nossa localização é</h1>
        <p>Pedro II - Piaui</p>
        <p>Rua Exemplo Do Nome Da Rua, 213 ,Quadra 12</p>

        <div id="map"></div>

    </div>
  </div>
</template>

<script>
  import L from 'leaflet';
import { Zoom } from 'swiper/modules';
  import { ref } from 'vue'


  export default {
  name: 'MapComponent',
  mounted() {
    // Criar o mapa
    const map = L.map('map').setView([-4.436539961556317, -41.45541510291524], 13);
    var greenIcon = L.icon({
    iconUrl: './IMG/livro-de-direito.png',

    iconSize:     [32, 32], // size of the icon
    shadowSize:   [50, 64], // size of the shadow
    iconAnchor:   [22, 94], // point of the icon which will correspond to marker's location
    shadowAnchor: [4, 62],  // the same for the shadow
    popupAnchor:  [-3, -76] // point from which the popup should open relative to the iconAnchor
});
    // Adicionar a camada de tiles
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      maxZoom: 19,
      minZoom: 15,
      attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map);

    // Adicionar um marcador
    const marker = L.marker([-4.436539961556317, -41.45541510291524], {icon: greenIcon}).addTo(map);
    marker.bindPopup("<b>Olá!</b><br>aqui é a praça.").openPopup();

    // Adicionar um círculo
    const circle = L.circle([-4.436747825229075, -41.454312439158386], {
      color: 'red',
      fillColor: '#f03',
      fillOpacity: 0.5,
      radius: 10
    }).addTo(map);
    circle.bindPopup("Uma referencia marcada.");

    // // Adicionar um polígono
    // const polygon = L.polygon([
    //   [51.509, -0.08],
    //   [51.503, -0.06],
    //   [51.51, -0.047]
    // ]).addTo(map);
    // polygon.bindPopup("I am a polygon.");

    // Evento de clique no mapa
    const popup = L.popup();

    function onMapClick(e) {
      popup
        .setLatLng(e.latlng)
        .setContent("Vocé clicou em " + e.latlng.toString())
        .openOn(map);
    }

    map.on('click', onMapClick);
  },
};

</script>

<style scoped>
.container{
  display: flex;
  justify-content: center;
  height: auto;
  background: #fffbff;
  color:black;
}
.local{
    display: flex;
    text-align: center;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    color:black;
    height: 50vh;
    width: 100%;
    margin-top:5rem;
    margin-bottom:5rem;
}
#map {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 40vh;
  width: 94%;
  border:4px solid black;
  border-radius: 20px;
  margin:10px;
}

</style>