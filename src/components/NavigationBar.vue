<script setup lang="ts">
import { ref, TransitionGroup } from "vue";

defineProps<{ current: number; sections: number }>();
</script>

<template>
  <Transition name="showNav">
    <nav class="navigation" v-if="current != 0">
      <TransitionGroup tag="div" name="select" class="list">
        <div
          class="element"
          v-for="section in sections"
          :key="section"
          :class="{ selected: current === section }"
          @click="$emit('scrollTo', section)"
        >
          <p>{{ section }}</p>
        </div>
      </TransitionGroup>
    </nav>
  </Transition>
</template>

<style scoped>
nav {
  position: fixed;
  top: 50%;
  left: 0;
  transform: translateY(-50%);
  margin-left: 1em;
  width: 50px;
  height: auto;
  background: rgba(36, 36, 36, 0.75);
  z-index: 10;
  border-radius: 250px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.list {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
  padding: 1rem 0;
  gap: 0.75rem;
}

.element {
  position: relative;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: radial-gradient(#4b85f8 10%, #8c85f3 100%);
  background-size: 150% 150%;
  background-position: 80% 80%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  transition: 0.25s;
}

.element p {
  opacity: 0;
  transition: 0.25s;
}

.element.selected {
  position: relative;
  width: 35px;
  height: 35px;
  border-radius: 50%;
  background: radial-gradient(#4b85f8 10%, #8c85f3 100%);
  background-size: 150% 150%;
  background-position: 90% 90%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.element.selected p {
  opacity: 1;
}

.showNav-enter-active,
.showNav-leave-active {
  transition: opacity 0.25s ease;
}

.showNav-enter-from,
.showNav-leave-to {
  opacity: 0;
}
</style>
