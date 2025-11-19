<script setup lang="ts">
import ScrollText from "./ScrollText.vue";
import sImage from "../assets/s-image.svg";
import jImage from "../assets/j-image.svg";
import mobileI from "../assets/mobile-icon.svg";
import desktopI from "../assets/desktop-icon.svg";
import { onMounted, onUnmounted, ref } from "vue";

const switchViewButtonToggle = ref(false);
const currentViewDesktop = ref(false);
const mouseOverButton = ref(false);
const mouseX = ref("");
const mouseY = ref("");
const buttonRef = ref<HTMLElement | null>(null);

function updateInsidePosition(event: MouseEvent) {
  if (!buttonRef.value) return;
  
  const rect = buttonRef.value.getBoundingClientRect();

  const relX = event.clientX - rect.left;
  const relY = event.clientY - rect.top;

  mouseX.value = relX + "px";
  mouseY.value = relY + "px";
}

</script>

<template>
  <section class="project-screen">
    <img class="info-panel-background-image" :src="jImage"/>
    <div class="project-info-panel">
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
        <div class="project-screen-size-select" ref="buttonRef" :class="{shown: switchViewButtonToggle}" @click="() => switchViewButtonToggle = !switchViewButtonToggle" @mouseover="() => mouseOverButton = true" @mouseout="() => mouseOverButton = false" @mousemove="updateInsidePosition">
            <h3>SWITCH VIEW MODE</h3>
            <Transition name="size-options">
              <div v-if="switchViewButtonToggle" class="project-size-options" @click.stop>
                <div class="project-type-view" :class="{selected: currentViewDesktop}" @click="() => currentViewDesktop = true">
                  <img :src="desktopI"/>
                  <div class="circle-select"></div>
                </div>
                <div class="project-type-view" :class="{selected: !currentViewDesktop}" @click="() => currentViewDesktop = false">
                  <img :src="mobileI"/>
                  <div class="circle-select"></div>
                </div>
              </div>
            </Transition>
            <Transition name="cursor-follower">
              <div
                v-if="mouseOverButton"
                class="cursor-follower"
                :style="{ left: mouseX, top: mouseY }"
              ></div>
            </Transition> 
        </div>
        <div class="project-description">
          <h1>In a nutshell</h1>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et <br></br><br></br>dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. <br></br><br></br> Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo.<br></br><br></br> Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla pariatur?</p>
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
    width: 275px;
    top: 0;
    left: 0;
    opacity: .3;
    mask-image: linear-gradient(to top, rgba(0,0,0,1), rgba(0,0,0,0));
    z-index: -1;
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
    width: 60%;
    height: 60%;
    border: 1px solid white;
    border-radius: 25px;
    background: rgba(217, 217, 217, .05);
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    padding: 1.5rem;
    overflow-y: scroll;
    box-shadow: inset -5px -20px 25px 10px rgba(25,25,25,.75);
}

.project-details::-webkit-scrollbar {
  width: 5px;
}

.project-details::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 50px;
  margin: 25px;
}

.project-details::-webkit-scrollbar-thumb {
  background: radial-gradient(#ac81ff, #0b84ff);
  border-radius: 50px;
}

.project-details::-webkit-scrollbar-thumb:hover {
  background: #555;
}

.project-screen-size-select {
    width: 100%;
    height: auto;
    box-shadow: 0 5px 10px 3px rgba(255, 255, 255,.25);
    border-radius: 25px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    font-family: "Urbanist", sans-serif;
    letter-spacing: .25rem;
    cursor: pointer;
    position: relative;
    overflow: hidden;
}

.project-screen-size-select h3 {
  user-select: none;
  pointer-events: none;
  transition: .5s;
  color: #f1f1f1;
}

.project-screen-size-select:hover h3 {
  color: black;
}

.project-screen-size-select.shown {
  background: #f1f1f1;
}

.project-screen-size-select.shown h3 {
  color: black;
}


.cursor-follower {
  position: absolute; /* relative to the button */
  width: 150px;
  height: 150px;
  background: white;
  border-radius: 100%;
  pointer-events: none;
  transform: translate(-50%, -50%) scale(5);
  z-index: -1;
}

/* ENTER */
.cursor-follower-enter-from {
  transform: translate(-50%, -50%) scale(0.2);
}

.cursor-follower-enter-to {
  transform: translate(-50%, -50%) scale(5);
}

.cursor-follower-enter-active {
  transition: transform 0.4s ease-in-out, opacity 0.25s ease-out;
}

/* LEAVE */
.cursor-follower-leave-from {
  transform: translate(-50%, -50%) scale(5);
}

.cursor-follower-leave-to {
  transform: translate(-50%, -50%) scale(0.2);
}

.cursor-follower-leave-active {
  transition: transform 0.4s ease-in, opacity 0.25s ease-in;
}

.project-size-options {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  gap: 1rem;
}

.project-type-view {
  border: 1px solid white;
  background: #252525;
  width: 6rem;
  height: 6rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: .25rem;
  padding: .5rem;
  border-radius: 15px;
  margin-bottom: 1.5rem;
  cursor: pointer;
  pointer-events: all;
  user-select: all;
  transition: .25s;
}

.project-type-view.selected .circle-select {
  background: #ac81ff;
}

.project-type-view:hover {
  transform: scale(1.05);
}

.project-type-view img {
  width: 100%;
  height: 5rem;
}

.project-type-view .circle-select {
  width: .75rem;
  height: .75rem;
  border-radius: 100%;
  background: white;
  transition: .25s;
}

.project-description {
  height: auto;
  position: relative;
}

.project-description h1 {
  height: auto;
  font-family: 'Urbanist', sans-serif;
  font-size: 2.5rem;
  margin: 1rem 0 0 0;
}

.project-description p {
  position: absolute;
  height: auto;
  font-family: 'Urbanist', sans-serif;
  font-weight: 600;
  margin: 0;
  z-index: -1;
  padding-bottom: 1.5rem;
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
  width: v-bind("currentViewDesktop ? '90%' : '30%'");
  height: 90%;
  background: #1b1b1b;
  border: 1px solid white;
  transition: .25s ease-in-out;
}

/* transition wrapper */
.size-options-enter-from,
.size-options-leave-to {
  opacity: 0;
  transform: scaleY(0.6);
  max-height: 0;
}

.size-options-enter-to,
.size-options-leave-from {
  opacity: 1;
  transform: scaleY(1);
  max-height: 200px;
}

.size-options-enter-active,
.size-options-leave-active {
  transition: all 0.35s ease;
  transform-origin: top;
}


</style>
