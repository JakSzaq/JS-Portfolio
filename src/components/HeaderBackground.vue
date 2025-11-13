<script setup lang="ts"></script>

<template>
  <section class="background">
    <div class="purple-light-source"></div>
    <div class="blue-light-source"></div>
    <div class="black-overlay"></div>
  </section>
</template>

<style>
.background {
  width: 100%;
  height: 100vh;
  background: linear-gradient(to bottom, #000000, #1b1b1b);
  position: relative;
  overflow: hidden;
}

.purple-light-source {
  position: absolute;
  top: 0;
  width: 100vw;
  height: 100vw;
  background: radial-gradient(#ac81ff 0%, rgba(0, 0, 0) 50%);
  opacity: 100%;
  background-size: 200% 200%;
  background-position: 80% 125%;
  background-repeat: no-repeat;
  mix-blend-mode: screen;
  animation: movePurpleLight 10s ease-in-out infinite both;
}

.blue-light-source {
  position: absolute;
  top: 0;
  width: 100vw;
  height: 100vw;
  background: radial-gradient(#0b84ff 0%, rgba(0, 0, 0) 60%);
  opacity: 100%;
  background-size: 150% 150%;
  background-position: 20% 200%;
  background-repeat: no-repeat;
  mix-blend-mode: screen;
  animation: moveBlueLight 15s ease-in-out infinite both;
}

.black-overlay {
  position: absolute;
  top: 0;
  width: 100vw;
  height: 100vw;
  background: black;
  opacity: 70%;
}

@keyframes movePurpleLight {
  0% {
    background-position: 80% 125%;
  }
  50% {
    background-position: 40% 70%;
  }
  100% {
    background-position: 80% 125%;
  }
}

@keyframes moveBlueLight {
  0% {
    background-position: 20% 200%;
  }
  50% {
    background-position: 60% 100%;
  }
  100% {
    background-position: 20% 200%;
  }
}
</style>
