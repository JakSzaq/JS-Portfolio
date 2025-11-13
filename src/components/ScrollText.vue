<script setup lang="ts"></script>

<template>
  <section class="scrollText">
    <h5>Scroll to interact</h5>
    <i class="fa-solid fa-arrow-down"></i>
  </section>
</template>

<style>
.scrollText {
  font-family: Comfortaa, sans-serif;
  font-weight: bold;
  color: white;
  font-size: 1.5em;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: row;
  gap: 1em;
}

.scrollText i {
  animation: arrowBounce 3s ease-in-out infinite both;
  transform: translateY(-5px);
}

@keyframes arrowBounce {
  0% {
    transform: translateY(-5px);
  }
  50% {
    transform: translateY(5px);
  }
  100% {
    transform: translateY(-5px);
  }
}
</style>
