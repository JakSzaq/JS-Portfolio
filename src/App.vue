<script setup lang="ts">
import { onMounted, onUnmounted, ref } from "vue";
import HeaderScreen from "./components/HeaderScreen.vue";
import NavigationBar from "./components/NavigationBar.vue";
import gsap from "gsap";
import _ScrollTrigger from "gsap/ScrollTrigger";

const currentlyVisible = ref(0); // 0 - header, 1-5 - projects
const sections = 5;

const scrollTo = (newVal: number) => {
  currentlyVisible.value = newVal;
  const el = document.querySelectorAll<HTMLElement>(".test")[newVal - 1];
  if (el) el.scrollIntoView({ behavior: "smooth" });
};

gsap.registerPlugin(_ScrollTrigger);

onMounted(() => {
  // Select all .test sections
  const testSections = gsap.utils.toArray<HTMLElement>(".test");

  // Create a ScrollTrigger for each section
  testSections.forEach((section, i) => {
    _ScrollTrigger.create({
      trigger: section,
      start: "top center", // when section top hits center of viewport
      end: "bottom center",
      onEnter: () => (currentlyVisible.value = i + 1),
      onEnterBack: () => (currentlyVisible.value = i + 1),
      onLeave: () => {}, // optional, could reset or handle leaving
      onLeaveBack: () => {}, // optional
    });
  });

  _ScrollTrigger.create({
    trigger: "header",
    start: "top center",
    end: "bottom center",
    onEnter: () => (currentlyVisible.value = 0),
    onEnterBack: () => (currentlyVisible.value = 0),
    onLeave: () => {},
    onLeaveBack: () => {},
  });
});

onUnmounted(() => {
  _ScrollTrigger.getAll().forEach((trigger) => trigger.kill());
});
</script>

<template>
  <HeaderScreen />
  <NavigationBar :current="currentlyVisible" :sections @scroll-to="scrollTo" />
  <div class="test" v-for="section in sections" :key="section">
    <h1>SECTION {{ section }}</h1>
  </div>
</template>

<style scoped>
.test {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

h1 {
}
</style>
