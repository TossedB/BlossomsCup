<template>
  <div style="height: 100%;" class="d-flex justify-content-center align-items-center">
    <div class="overlay">
    </div>
    <div class="content">
      <h1 class="mb-5">BLOSSOMS CUP 1</h1>
      <div class="d-flex justify-content-between">
        <PlayerCard v-if="players.length === 2" :player="players[0]"></PlayerCard>
        <BarChart v-if="players.length === 2" class="me-4" :players="players"></BarChart>
        <PlayerCard v-if="players.length === 2" class="ms-5" :player="players[1]"></PlayerCard>
      </div>
      <input v-model="pInput" @input="fillPlayers"/>
    </div>
  </div>
</template>

<script setup>
import {ref} from 'vue'
import BarChart from './components/BarChart.vue'
import PlayerCard from './components/PlayerCard.vue'

const players = ref([])
const pInput = ref()
const fillPlayers = () => {
  try {
    players.value = JSON.parse(pInput.value)
  } catch (e) {
    players.value = []
  }
}
</script>

<style>
input {
  width: 100%;
  padding: 12px 20px;
  box-sizing: border-box;
  background: rgba(0, 0, 0, 0.5)
}

#app {
  width: 100vw;
  height: 100vh;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: rgb(14,15,14);
    /* background: linear-gradient(0deg, rgba(57,0,64,1) 4%, rgba(14,15,14,1) 30%);  */
  background-image: url('@/assets/background.png');
  background-repeat: no-repeat;
  position: relative;
  background-size: stretch;
}

html {
  padding: 0;
  margin: 0;
}

body {
  padding: 0;
  margin: 0;
  overflow-x: hidden;
}

.overlay {
  content: ('');
  display: block;
  position: absolute;
  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
  background: linear-gradient(0deg, rgba(14,15,14, 0.8) 40%, rgba(57,0,64, 0.5) 100% ); 
  z-index: 1;
}

.content {
  z-index: 2;
}

@font-face {
    font-family: "Blanka-Regular";
    src: url("https://db.onlinewebfonts.com/t/8cdbb48678e4418f22a2f507c2b975bd.eot");
    src: url("https://db.onlinewebfonts.com/t/8cdbb48678e4418f22a2f507c2b975bd.eot?#iefix")format("embedded-opentype"),
    url("https://db.onlinewebfonts.com/t/8cdbb48678e4418f22a2f507c2b975bd.woff2")format("woff2"),
    url("https://db.onlinewebfonts.com/t/8cdbb48678e4418f22a2f507c2b975bd.woff")format("woff"),
    url("https://db.onlinewebfonts.com/t/8cdbb48678e4418f22a2f507c2b975bd.ttf")format("truetype"),
    url("https://db.onlinewebfonts.com/t/8cdbb48678e4418f22a2f507c2b975bd.svg#Blanka-Regular")format("svg");
}

h1 {
  font-family: "Blanka-Regular"; 
  color: #390040;
  -webkit-text-fill-color: #390040; /* Will override color (regardless of order) */
  -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: #ce10fa;
  font-size: 5em;
}

@font-face {
    font-family: "Now";
    src: url("https://db.onlinewebfonts.com/t/903ebe10b757dc8185071c84b359f5fd.eot");
    src: url("https://db.onlinewebfonts.com/t/903ebe10b757dc8185071c84b359f5fd.eot?#iefix")format("embedded-opentype"),
    url("https://db.onlinewebfonts.com/t/903ebe10b757dc8185071c84b359f5fd.woff2")format("woff2"),
    url("https://db.onlinewebfonts.com/t/903ebe10b757dc8185071c84b359f5fd.woff")format("woff"),
    url("https://db.onlinewebfonts.com/t/903ebe10b757dc8185071c84b359f5fd.ttf")format("truetype"),
    url("https://db.onlinewebfonts.com/t/903ebe10b757dc8185071c84b359f5fd.svg#Now")format("svg");
}

</style>
