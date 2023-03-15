
<template>
  <q-page>
    <div id="youmap" style="width: 100%; height: 500px"></div>
  </q-page>
</template>

<script setup>
import { onMounted } from "vue";
import L from "leaflet";
import "leaflet/dist/leaflet.css";

function locationYou() {
  var map = L.map("youmap").fitWorld();

  L.tileLayer(
    "http://api.mapbox.com/styles/v1/mapbox/{id}/tiles/{z}/{x}/{y}?access_token={accessToken}",
    {
      maxZoom: 19,
      attribution:
        '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
      id: "streets-v12",
      accessToken:
        "pk.eyJ1IjoiZWR3aW4yNDAxIiwiYSI6ImNsZjdydmpncTA4bDMzcW8xYmcydXprZ3EifQ.l_l09OyNgR4OVFUygdWYGA",
    }
  ).addTo(map);

  map.locate({ setView: true, maxZoom: 40, watch: true, timeout: 6000 });

  function getcurrentYouLocation(e) {
    alert("lat is:" + e.latlng.lat + "long" + e.latlng.lng); //agregamos las coordenadas
    var radius = e.acurracy;
    L.marker(e.latlng)
      .addTo(map)
      .bindPopup("estas aqui " + radius + "en estas coordenadas")
      .openPopup();
    //popup nuesta ubicacion en un cuadro
    L.circle(e.latlng, radius).addTo(map);
  }
  function onLocationError(e) {
    alert(e.message);
  }
  //detect location
  map.on("locationfound", getcurrentYouLocation);
}

onMounted(() => {
  locationYou();
});
</script>
