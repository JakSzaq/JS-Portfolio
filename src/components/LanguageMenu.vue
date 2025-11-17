<script setup lang="ts">
import { ref, type Ref } from "vue";

const changedLanguage: Ref<Boolean> = ref(false);

const changeLanguage = (newLang: boolean) => {
  changedLanguage.value = newLang;
};
</script>

<template>
  <div class="lang-menu">
    <h4 @click="changeLanguage(false)" :class="{ selected: !changedLanguage }">
      EN
    </h4>
    <div class="separator"></div>
    <h4 @click="changeLanguage(true)" :class="{ selected: changedLanguage }">
      PL
    </h4>
  </div>
</template>

<style scoped>
.lang-menu {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: row;
  width: 150px;
  font-size: 3em;
  margin-top: 10px;
}

.lang-menu * {
  margin: 0;
  font-family: Outfit, sans-serif;
  font-weight: bold;
  color: white;
}

.lang-menu .separator {
  width: 1px;
  background: white;
  height: 80%;
}

.lang-menu h4 {
  background: radial-gradient(#ffffff 40%, #ac81ff 40%, #0b84ff);
  background-size: 400% 400%;
  background-position: 50% 50%;
  background-repeat: no-repeat;
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  transition: 0.25s;
  cursor: pointer;
  user-select: none;
}

.lang-menu .selected {
  background: radial-gradient(#ffffff 40%, #ac81ff 40%, #0b84ff);
  background-size: 400% 400%;
  background-position: 90% 100%;
  background-repeat: no-repeat;
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  transition: 0.25s;
  cursor: pointer;
  user-select: none;
}

.lang-menu h4:hover {
  background-position: 50% 100%;
}

.lang-menu .selected:hover {
  background-position: 50% 100%;
}
</style>
