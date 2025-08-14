<script setup>
import { onUpdated, ref } from 'vue';
import { useRouter } from 'vue-router';

const props = defineProps({
  target: String
})
const getBorderClass = (targetPath) => {
  return props.target === targetPath ? 'border-b-3px border-white' : ' border-b-3px duration-800 border-transparent hover:border-[rgba(255,255,255,0.5)]';
}
const getMenuBorderClass = (targetPath) => {
  return props.target === targetPath ? 'bg-white ' : 'bg-transparent hover-bg-[rgba(255,255,255,0.5)]'
}
const router = useRouter();
const IsOpen = ref(false);
</script>
<template>
  <header>
    <div id="menu" class="transition-800" :class="IsOpen ? 'open' : 'close'">
      <div class="w-100% absolute left-85% cursor-pointer" @click="() => IsOpen = false">
        <img src="/src/assets/home/close.svg" alt="">
      </div>
      <div class="mt-80px h-222px flex flex-col justify-between items-end">
        <div @click="() => router.push('/')" class="w-90% flex justify-between group">
          <div><span class="barlow-text text-16px font-bold text-white mr-12px">00</span><span
              class="barlow-text text-16px text-white">HOME</span></div>
          <div class="w-5px h-100% group-hover:bg-[rgba(255,255,255,0.5)] transition-800"
            :class="getMenuBorderClass('/')"></div>
        </div>
        <div @click="() => router.push('/destination')" class=" w-90% flex justify-between group">
          <div><span class="barlow-text text-16px font-bold text-white mr-12px">01</span><span
              class="barlow-text text-16px text-white">DESTINATION</span></div>
          <div class="w-5px h-100% group-hover:bg-[rgba(255,255,255,0.5)] transition-800"
            :class="getMenuBorderClass('/destination')"></div>
        </div>
        <div @click="() => router.push('/crew')" class="w-90% flex justify-between group">
          <div><span class="barlow-text text-16px font-bold text-white mr-12px">02</span><span
              class="barlow-text text-16px text-white">CREW</span></div>
          <div class="w-5px h-100% group-hover:bg-[rgba(255,255,255,0.5)] transition-800"
            :class="getMenuBorderClass('/crew')"></div>
        </div>
        <div @click="() => router.push('/technology')" class="w-90% flex justify-between group">
          <div><span class="barlow-text text-16px font-bold text-white mr-12px">03</span><span
              class="barlow-text text-16px text-white">TECHNOLOGY</span></div>
          <div class="w-5px h-100% group-hover:bg-[rgba(255,255,255,0.5)] transition-800"
            :class="getMenuBorderClass('/technology')"></div>
        </div>
      </div>
    </div>
    <nav class="miniNav flex h-100% items-center">
      <div id="part1" class="md:w-51% w-16.6667% h-fit flex items-center z-1">

        <div class="flex-1 text-center"><img id="pic" src="../assets/shared/logo.svg" alt=""></div>
        <div class="w-76.08% h-1px bg-white/25 md:block hidden"></div>
      </div>
      <div id="part2" @click="() => IsOpen = true"><img src="/src/assets/home/menu.svg" alt=""></div>
      <div id="navMenu"
        class="md:w-51% w-83.3333% nav2 h-100% md:ml-[-2.2%] sm:ml-0 flex items-center justify-unset xl:justify-start">
        <RouterLink to="/"
          class="transition  content-center h-95% border-solid border-0 decoration-none md:ml-21.6% ml-18.28% md:mr-6.5% mr-48px barlow-text font-bold tracking-[2.7px] text-white"
          :class="getBorderClass('/')">
          <div class="xl:text-16px text-12px">00<span
              class="xl:ml-12px ml-6px barlow-text tracking-[2px] xl:text-16px text-12px font-normal">HOME</span></div>
        </RouterLink>
        <RouterLink to="/destination"
          class="transition content-center h-95% border-solid border-0 md:mr-6.5% mr-48px barlow-text font-bold tracking-[2.7px] text-white decoration-none"
          :class="getBorderClass('/destination')">
          <div class="xl:text-16px text-12px">01<span
              class="xl:ml-12px ml-6px barlow-text tracking-[2px] xl:text-16px text-12px font-normal">DESTINATION</span>
          </div>
        </RouterLink>
        <RouterLink to="/crew"
          class="content-center h-95% border-solid border-0 decoration-none text-white md:mr-6.5% mr-48px barlow-text font-bold tracking-[2.7px]"
          :class="getBorderClass('/crew')">
          <div class="xl:text-16px text-12px">02<span
              class="xl:ml-12px ml-6px barlow-text tracking-[2px] xl:text-16px text-12px font-normal">CREW</span>
          </div>
        </RouterLink>
        <RouterLink to="/technology"
          class="content-center h-95% border-solid border-0 decoration-none text-white barlow-text font-bold tracking-[2.7px]"
          :class="getBorderClass('/technology')">
          <div class="xl:text-16px text-12px">03<span
              class="xl:ml-12px ml-6px barlow-text xl:text-16px text-12px tracking-[2px] font-normal">TECHNOLOGY</span>
          </div>
        </RouterLink>
      </div>
    </nav>
  </header>
</template>
<style scoped>
header {
  height: 136px;
  padding-top: 40px;
  box-sizing: border-box;
}

.nav2 {
  background-color: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(30px);
  min-width: fit-content;
}

#pic {
  width: 48px;
}

#menu {
  display: none;
}

#part2 {
  display: none;
}

@media (max-width:376px) {
  #navMenu {
    display: none;
  }

  #part2 {
    display: block;
  }

  #pic {
    width: 40px;
  }

  #part1 {
    width: fit-content;
    color: white;
  }

  .miniNav {
    width: 100%;
    display: flex;
    justify-content: space-between;
    padding: 0 10px;
    box-sizing: border-box;
  }

  #menu {
    display: block;
    position: fixed;
    height: 120vh;
    width: 67.733%;
    right: 0;
    top: 0;
    backdrop-filter: blur(40px);
    z-index: 99;
    padding-top: 20px;
  }

  .close {
    transform: translateX(100%);
  }

  .open {
    transform: translateX(0);
  }
}
</style>
