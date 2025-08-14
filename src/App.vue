<script setup>
import { RouterLink, RouterView, useRoute } from 'vue-router'
import Header from "./components/Header.vue";
import { nextTick, onMounted, onUpdated, ref } from 'vue';
const route = useRoute();
const path = ref({
  "/": "url('/src/assets/home/background-home-desktop.jpg')",
  "/destination": "url('/src/assets/destination/background-destination-desktop.jpg')",
  "/crew": "url('/src/assets/crew/background-crew-desktop.jpg')",
  "/technology": "url('/src/assets/technology/background-technology-desktop.jpg')"
})
const onBeforeEnter = () => {
  const width = window.innerWidth
  if (width < 768 && route.path === "/") {
    document.body.style.backgroundImage = "url('/src/assets/home/background-home-tablet.jpg')"
  } else {
    document.body.style.backgroundImage = path.value[route.path];
  }
}
onMounted(() => {
  window.addEventListener("resize", onBeforeEnter)
})
onUpdated(() => {
  onBeforeEnter();
})
</script>

<template>
  <div id="main">
    <Header :target="route.path"></Header>
    <RouterView v-slot="{ Component }">
      <transition name="fade" mode="out-in" @before-leave="onBeforeEnter">
        <component :is="Component" />
      </transition>
    </RouterView>
  </div>

</template>

<style>
#main {
  display: flex;
  min-width: fit-content;
  flex-direction: column;
  flex: 1;
}


.barlow-text {
  font-family: 'Barlow Condensed',
    sans-serif;
}

.bellefair-text {
  font-family: 'Bellefair', serif;
}

body {
  background-image: url('./assets/home/background-home-desktop.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  background-attachment: fixed;
  transition: 0.5s ease-out;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* 加上這行就解決了 */
.fade-leave-from {
  opacity: 1;
}

@media (min-width: 375px)and (max-width:768px) {
  body {
    background-image: url('./assets/home/background-home-tablet.jpg');
  }
}
</style>
