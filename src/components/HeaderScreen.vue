<script setup lang="ts">
import HeaderBackground from "./HeaderBackground.vue";
import HeaderContent from "./HeaderContent.vue";
</script>

<template>
  <header>
    <HeaderBackground />
    <HeaderContent />
  </header>
</template>

<style scoped>
header {
  width: 100%;
  height: 100vh;
  position: relative;
}
</style>
