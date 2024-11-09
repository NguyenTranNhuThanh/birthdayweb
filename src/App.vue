<script setup lang="ts">
import { onMounted } from 'vue';

let text:HTMLImageElement;
onMounted(() => {
  text = document.getElementById("text")! as HTMLImageElement;
});

function SpawnPresent()
{
  if (Math.random() < 0.3)
  {
    let present:HTMLImageElement = document.createElement("img");
    present.style.position = "fixed";
    present.src = "/present.png";
    present.style.left = Math.random() * 120 + "%";
    present.animate([{top: "-50%"}, {top: "100%", rotate: "360deg"}], {iterations: Infinity, duration: 5000});
    text.insertAdjacentElement("beforebegin", present);

    setTimeout(() => {present.remove()}, 5000);
  }
}

setInterval(SpawnPresent, 500);
</script>

<template>
  <img id="grid" src="/grid.png">
  <img id="text" src="/text.png">
  <img id="cloudYellow" src="/cloudYellow.png">
  <img id="cloudWhite" src="/cloudWhite.png">
  <img id="cake" src="/cake.png">
</template>

<style scoped>
  #grid {
    position: fixed;
    
    min-width: 100%;
    top: -1.6%;

    animation-name: slide;
    animation-duration: 20s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
  }

  #cloudYellow {
    position: absolute;
    
    min-width: 100%;
    top: 67.8%;

    animation-name: slide;
    animation-duration: 15s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
  }

  #cloudWhite {
    position: absolute;
    
    min-width: 100%;
    top: 83%;

    animation-name: slide;
    animation-duration: 15s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
    animation-direction: reverse;
  }

  #text {
    position: absolute;

    top: 3%;
    left: 22.3%;

    animation-name: wiggle;
    animation-duration: 7s;
    animation-timing-function: ease-in-out;
    animation-iteration-count: infinite;
  }

  #cake {
    position: absolute;

    top: 35%;
    left: 33%;

    animation-name: wiggle;
    animation-duration: 5s;
    animation-timing-function: ease-in-out;
    animation-iteration-count: infinite;
  }

  @keyframes wiggle {
    0% {
      rotate: -5deg;
    }
    50% {
      rotate: 5deg;
    }
    100% {
      rotate: -5deg;
    }
  }

  @keyframes slide {
    0% {
      left: 0%;
    }
    100% {
      left: -71.1%;
    }
  }
</style>