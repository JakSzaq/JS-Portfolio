<script setup lang="ts">
import logo from "../assets/logo.svg";
</script>

<template>
  <section class="center">
    <div class="left">
      <svg
        width="414"
        height="504"
        viewBox="0 0 414 504"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          id="logo-plain"
          d="M146.984 308.775C93.5811 306.291 46.3481 340.824 37.1582 359.659C37.0404 359.901 37.0112 360.112 37.1192 360.358C46.2592 381.176 210.216 489.509 314.673 484.922C315.005 484.908 315.28 484.773 315.429 484.475C330.791 453.681 130.778 193.973 221.984 69.3857C291.846 -16.9364 421.346 23.6483 389.484 69.3857C262.844 251.174 5.82141 155.78 19.2604 25.6141C19.3442 24.8029 20.2984 24.4197 20.8637 25.0077C38.4759 43.3269 65.8461 108.022 36.6215 178.648"
          stroke="white"
          stroke-width="37.5"
          stroke-linecap="round"
        />
      </svg>
      <img :src="logo" />
    </div>
    <div class="right">
      <h3>Portfolio of</h3>
      <h1>Jakub Szafryk</h1>
    </div>
  </section>
</template>

<style>
.left {
  height: 100px;
  position: relative;
}

.left img,
.left svg {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.left img {
  position: absolute;
  top: 0;
  left: 0;
  opacity: 0;
  animation: showElement 1s ease-in-out forwards 2s;
}

.left svg #logo-plain {
  stroke-dasharray: 1750;
  stroke-dashoffset: -1750;
  animation: drawLogo 1s ease-in-out forwards, hideElement 1s linear forwards 2s;
}

@keyframes drawLogo {
  to {
    stroke-dashoffset: 0;
  }
}

@keyframes showElement {
  to {
    opacity: 1;
  }
}

@keyframes hideElement {
  to {
    opacity: 0;
  }
}

.right {
  height: 100px;
  color: white;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-direction: column;
}

.center {
  width: 500px;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-direction: row;
  font-family: Comfortaa, sans-serif;
  font-weight: bold;
  gap: 1em;
  line-height: 2em;
  transform: translateX(140px);
  animation: slideInHeader 1s ease-in-out forwards 1s;
}

@keyframes slideInHeader {
  to {
    transform: translateX(0px);
  }
}

.center h1,
.center h3 {
  text-transform: uppercase;
  margin: 0;
  opacity: 0;
  animation: showElement 1s ease-in-out forwards 2s;
}
</style>
