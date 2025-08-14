<script setup>
import { computed, ref } from "vue";

const totalPage = ref([{
  id: 1,
  title: 'COMMANDER',
  crew: 'DOUGLAS HURLEY',
  detail: 'Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA astronaut.He launched into space for the third time as commander of Crew Dragon Demo- 2.',
  pic: './src/assets/crew/image-douglas-hurley.png'
}, {
  id: 2,
  title: 'MISSION SPECIALIST ',
  crew: 'MARK SHUTTLEWORTH',
  detail: 'Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind the Linux-based Ubuntu operating system. Shuttleworth became the first South African to travel to space as a space tourist.',
  pic: './src/assets/crew/image-mark-shuttleworth.png'
}, {
  id: 3,
  title: 'PILOT',
  crew: 'VICTOR GLOVER',
  detail: 'Pilot on the first operational flight of the SpaceX Crew Dragon to the International Space Station. Glover is a commander in the U.S. Navy where he pilots an F/A-18.He was a crew member of Expedition 64, and served as a station systems flight engineer.',
  pic: './src/assets/crew/image-victor-glover.png'
}, {
  id: 4,
  title: 'FLIGHT ENGINEER',
  crew: 'ANOUSHEH ANSARI',
  detail: 'Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems. Ansari was the fourth self-funded space tourist, the first self-funded woman to fly to the ISS, and the first Iranian in space.',
  pic: './src/assets/crew/image-anousheh-ansari.png'
}]);
const currentPage = ref(1);
</script>
<template>
  <div class="containerA">
    <div class="mb-24px xs-span-center">
      <span
        class="span-text-rwd barlow-text font-bold tracking-4.72px text-28px text-[rgba(255,255,255,0.25)] mr-24px">02</span><span
        class="span-text-rwd barlow-text text-white text-28px tracking-4px">MEET YOUR CREW</span>
    </div>
    <div
      class="flex md:flex-row flex-col h-734px mt-64px md:mt-0 items-center md:items-unset w-100% md:w-unset absolute md:pos-unset left-0 md:left-unset">
      <div class="md:w-48.559% w-100% h-100% flex flex-col box-border ">
        <div class="flex-1 w-100% flex items-center relative">
          <Transition name="wade">
            <div :key="currentPage" class="absolute">
              <div
                class="bellefair-text title-text-rwd text-[rgba(255,255,255,0.5042)] mb-16px text-center md:text-start">
                {{
                  totalPage[currentPage - 1].title }}</div>
              <div class="text-center md:text-start bellefair-text crew-text-rwd text-white my-24px">{{
                totalPage[currentPage - 1].crew }}
              </div>
              <div
                class="text-center md:text-start w-100% barlow-text md:text-18px text-16px line-height-[180%] text-[#D0D6F9] box-border px-15% md:px-0">
                {{
                  totalPage[currentPage
                    -
                    1].detail
                }}
              </div>
            </div>
          </Transition>
        </div>
        <!-- page導航 -->
        <div
          class="h-8.583% w-100% flex no-transition md:mt-60px mt-0px justify-around md:justify-unset px-40% md:px-0 box-border">
          <div v-for="item in totalPage" :key="item.id"
            class="md:w-15px w-10px md:h-15px h-10px rounded-100% bg-[rgba(255,255,255,0.1744)] md:mr-40px mr-0 cursor-pointer transition-400"
            :class="currentPage === item.id ? 'bg-white' : 'hover-bg-[rgba(255,255,255,0.5)]'"
            @click="currentPage = item.id">
          </div>
        </div>
        <!-- page導航 -->
      </div>
      <div class="w-2.882%"></div>
      <div class="w-48.559% relative h-100%  py-29px box-border flex justify-center">
        <Transition name="wade">
          <img class="sid absolute" :key="currentPage" :src="totalPage[currentPage - 1].pic" alt="" height="90%">
        </Transition>
      </div>
    </div>

  </div>
</template>
<style scoped>
.containerA {
  box-sizing: border-box;
  width: 100%;
  height: 888px;
  padding: 48px 11.45%;
}

.sid {
  mask-image: linear-gradient(to bottom, rgba(0, 0, 0, 1) 80%, rgba(0, 0, 0, 0) 100%);
}

.wade-enter-active,
.wade-leave-active {
  transition: 0.3s ease;
}

.wade-enter-from,
.wade-leave-to {
  opacity: 0;
}

.wade-enter-to,
.wade-leave-from {
  opacity: 1;
}

.no-transition {
  transition: none !important;
  opacity: 1 !important;
}

.title-text-rwd {
  font-size: 32px;
}

.crew-text-rwd {
  font-size: 56px;
}

@media (min-width: 377px) and (max-width:768px) {
  .span-text-rwd {
    font-size: 20px;
  }

  .containerA {
    padding: 48px 5.45%;
  }

  .title-text-rwd {
    font-size: 24px;
  }

  .crew-text-rwd {
    font-size: 40px;
  }
}

@media (max-width: 376px) {
  .span-text-rwd {
    font-size: 16px;
  }

  .xs-span-center {
    text-align: center;
  }

  .containerA {
    padding: 48px 10.45%;
  }

  .title-text-rwd {
    font-size: 18px;
  }

  .crew-text-rwd {
    font-size: 24px;
  }
}
</style>
