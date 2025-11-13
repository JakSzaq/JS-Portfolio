<script setup lang="ts">
import AnimatedText from "./AnimatedText.vue";
import LanguageMenu from "./LanguageMenu.vue";
import ScrollText from "./ScrollText.vue";
</script>

<template>
  <section class="content">
    <LanguageMenu />
    <AnimatedText />
    <ScrollText />
  </section>
</template>

<style>
.content {
  position: absolute;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
}
</style>
