<script setup lang="ts">
import ScrollText from "./ScrollText.vue";
import sImage from "../assets/s-image.svg";
import jImage from "../assets/j-image.svg";
</script>

<template>
  <section class="project-screen">
    <div class="project-info-panel">
      <img class="info-panel-background-image" :src="jImage"></img>
      <div class="project-header">
        <div class="project-title">
        <h1>TEST</h1>
        <i class="fa-solid fa-location-dot"></i>
      </div>
      <div class="project-subtitle">
        <h2>Lorem ipsum dolor</h2>
      </div>
      </div>
      <div class="project-details">
        <div class="project-screen-size-select">
            <h3>SWITCH VIEW MODE</h3>
        </div>
      </div>
      <ScrollText />
    </div>
    <div class="project-interface">
      <img class="interface-background-image" :src="sImage"></img>
      <div class="project-view"></div>
    </div>
  </section>
</template>

<style scoped>
.project-screen {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #1b1b1b;
}

.project-info-panel {
  width: 30%;
  height: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  flex-direction: column;
  position: relative;
  z-index: 1;
  overflow: hidden;
}

.info-panel-background-image {
    position: absolute;
    width: 50%;
    top: 0;
    left: 0;
    opacity: .3;
    mask-image: linear-gradient(to top, rgba(0,0,0,1), rgba(0,0,0,0));
    z-index: 0;
}

.project-title {
    display: flex;
    justify-content: center;
    flex-direction: row;
    gap: 1rem;
}

.project-title h1 {
    font-size: 4rem;
    margin: 0;
}

.project-subtitle h2 {
    margin: 0;
    line-height: .5rem;
    font-weight: 500;
}

.project-title i {
    font-size: 4rem;
    line-height: 6rem;
    color: #ac81ff;
}

.project-details {
    width: 70%;
    height: 75%;
    border: 2px solid white;
    border-radius: 25px;
    background: rgba(217, 217, 217, .05);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.project-screen-size-select {
    width: 90%;
    height: 225px;
    box-shadow: 0 5px 5px 5px rgba(255, 255, 255,.25);
    border-radius: 25px;
    display: flex;
    justify-content: center;
    font-family: "Urbanist", sans-serif;
    letter-spacing: .25rem;
}

.project-interface {
  width: 70%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.interface-background-image {
  position: absolute;
  width: 100%;
  height: 100%;
  rotate: 30deg;
  transform: scale(2.1);
  opacity: .1;
}

.project-view {
  position:absolute;
  padding: 2rem;
  width: 30%;
  height: 90%;
  background: #1b1b1b;
  border: 3px solid black;
}
</style>
