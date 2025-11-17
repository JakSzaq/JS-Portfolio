<script setup lang="ts">
import { onMounted, onUnmounted, ref } from "vue";
import HeaderScreen from "./components/HeaderScreen.vue";
import NavigationBar from "./components/NavigationBar.vue";
import ProjectShowcase from "./components/ProjectShowcase.vue";
import gsap from "gsap";
import _ScrollTrigger from "gsap/ScrollTrigger";

const currentlyVisible = ref(0); // 0 - header, 1-5 - projects
const sections = 5;

const scrollTo = (newVal: number) => {
  const el =
    document.querySelectorAll<HTMLElement>(".projectSections")[newVal - 1];
  if (el) el.scrollIntoView({ behavior: "smooth" });
};

gsap.registerPlugin(_ScrollTrigger);

onMounted(() => {
  const projectSections = gsap.utils.toArray<HTMLElement>(".projectSections");

  projectSections.forEach((section, i) => {
    _ScrollTrigger.create({
      trigger: section,
      start: "top center",
      end: "bottom center",
      onEnter: () => (currentlyVisible.value = i + 1),
      onEnterBack: () => (currentlyVisible.value = i + 1),
      onLeave: () => {},
      onLeaveBack: () => {},
    });

    _ScrollTrigger.create({
      trigger: section,
      start: "top 25%",
      end: "bottom 75%",
      onEnter: () => {
        gsap.killTweensOf(section);
        gsap.to(section, {
          opacity: 1,
          y: 0,
          duration: 0.6,
          ease: "power2.out",
        });
        gsap.fromTo(
          ".project-info-panel",
          { x: -100, opacity: 0 },
          { x: 0, opacity: 1, duration: 0.6, delay: 0 }
        );
        gsap.fromTo(
          ".project-interface",
          { x: 100, opacity: 0 },
          { x: 0, opacity: 1, duration: 0.6, delay: 0.3 }
        );
      },
      onEnterBack: () => {
        gsap.killTweensOf(section);
        gsap.to(section, {
          opacity: 1,
          y: 0,
          duration: 0.6,
          ease: "power2.out",
        });
        gsap.fromTo(
          ".project-info-panel",
          { x: -100, opacity: 0 },
          { x: 0, opacity: 1, duration: 0.6, delay: 0 }
        );
        gsap.fromTo(
          ".project-interface",
          { x: 100, opacity: 0 },
          { x: 0, opacity: 1, duration: 0.6, delay: 0.3 }
        );
      },
      onLeave: () => {
        gsap.killTweensOf(section);
        gsap.to(section, {
          opacity: 0,
          y: -25,
          duration: 0.6,
          ease: "power2.in",
        });
      },
      onLeaveBack: () => {
        gsap.killTweensOf(section);
        gsap.to(section, {
          opacity: 0,
          y: 25,
          duration: 0.6,
          ease: "power2.in",
        });
      },
    });
  });

  _ScrollTrigger.create({
    trigger: "header",
    start: "top center",
    end: "bottom center",
    onEnter: () => (currentlyVisible.value = 0),
    onEnterBack: () => (currentlyVisible.value = 0),
  });

  _ScrollTrigger.create({
    snap: {
      snapTo: (progress) => {
        const total = sections;
        return Math.round(progress * total) / total;
      },
      duration: 1.2,
      ease: "power2.inOut",
    },
  });
});

onUnmounted(() => {
  _ScrollTrigger.getAll().forEach((trigger) => trigger.kill());
});
</script>

<template>
  <div class="smooth-scroll">
    <HeaderScreen />
    <NavigationBar
      :current="currentlyVisible"
      :sections
      @scroll-to="scrollTo"
    />
    <ProjectShowcase
      class="projectSections"
      v-for="section in sections"
      :key="section"
    />
  </div>
</template>

<style scoped></style>
