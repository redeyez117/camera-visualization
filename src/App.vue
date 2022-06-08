<script setup>

import Camera from "./components/Camera.vue";
import {computed, ref} from "vue";

const positionCamera1 = computed(()=>{
  return {
    top:'30%',
    right:'21%',
    transform:'rotate(-25deg)',
  }
})

const positionCamera2 = computed(()=>{
  return {
    top:'40%',
    right:'45%',
    transform:'rotate(192deg)'
  }
})

const positionCamera3 = computed(()=>{
  return {
    bottom:'23%',
    left:'49%',
    transform:'rotate(-130deg)'
  }
})

const positionCamera4 = computed(()=>{
  return {
    top:'50%',
    left:'30%',
    transform:'rotate(-80deg)'
  }
})

const showOverlay = ref('none')
const cameraImage = ref('')

const showCamera = (camera) => {
  cameraImage.value = camera
}
</script>

<template>
  <main class="camera-background">
    <div :style="{display:showOverlay}" class="overlay"></div>
    <Camera @click="showCamera('./src/assets/img1.jpeg')" @mouseover="showOverlay = 'block'" @mouseleave="showOverlay = 'none'" id="camera1" title="01" :position="positionCamera1">
      <p class="camera1">01</p>
    </Camera>
    <Camera @click="showCamera('./src/assets/img2.jpeg')" @mouseover="showOverlay = 'block'" @mouseleave="showOverlay = 'none'" title="02" :position="positionCamera2">
      <p class="camera2">02</p>
    </Camera>
    <Camera @click="showCamera('./src/assets/img3.jpeg')" @mouseover="showOverlay = 'block'" @mouseleave="showOverlay = 'none'" title="03" :position="positionCamera3">
      <p class="camera3">03</p>
    </Camera>
    <Camera @click="showCamera('./src/assets/img4.jpeg')" @mouseover="showOverlay = 'block'" @mouseleave="showOverlay = 'none'" title="04" :position="positionCamera4">
      <p class="camera4">04</p>
    </Camera>
    <div v-if="cameraImage.length > 1" class="camera-image">
      <img :src="cameraImage" class="image"/>
    </div>
  </main>
</template>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding:0 5rem;
  font-weight: normal;

}

.camera-background {
  width: 100%;
  height: 100vh;
  background: url("./src/assets/map.png");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  overflow: hidden;
}

.overlay {
  position: absolute;
  z-index:2;
  background: rgb(35, 32, 32);
  top: 0;
  width: 100%;
  height: 100%;
  opacity: 0.6;
}

.camera1 {
  transform: rotate(25deg);
  transform-origin: 50% 50%;
  margin: 0 auto;
}

.camera2 {
  transform: rotate(169deg);
  transform-origin: 50% 50%;
  margin: 0 auto;
}

.camera3 {
  transform: rotate(130deg);
  transform-origin: 50% 50%;
  margin: 0 auto;
}

.camera4 {
  transform: rotate(80deg);
  transform-origin: 50% 50%;
  margin: 0 auto;
}

.camera-image {
  position: absolute;
  bottom: 0px;
  width: 300px;
  height: 150px;
}

.image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
