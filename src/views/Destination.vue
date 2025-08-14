<script setup>
import { ref } from 'vue';
const currentTarget = ref(1);
const TargetClass = (target) => {
  return currentTarget.value === target ? "border-white !text-white" : "transition duration-800 hover:border-[rgba(255,255,255,0.5)] hover:text-white"
}
const planet = ref([{
  name: "moon",
  id: 1,
  img: "/src/assets/destination/image-moon.png",
  description: "See our planet as you’ve never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you’re there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.",
  distance: "384,400 km",
  travelTime: "3 DAYS"
}, {
  name: "mars",
  id: 2,
  img: "/src/assets/destination/image-mars.png",
  description: "Don’t forget to pack your hiking boots. You’ll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It’s two and a half times the size of Everest!",
  distance: "225 MIL. KM",
  travelTime: "9 MONTHS"
}, {
  name: "europa",
  id: 3,
  img: "/src/assets/destination/image-europa.png",
  description: "The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover’s dream. With an icy surface, it’s perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.", distance: "628 MIL. KM",
  travelTime: "3 YEARS"
}, {
  name: "titan",
  id: 4,
  img: "/src/assets/destination/image-titan.png",
  description: "The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.",
  distance: "1.6 BIL. KM",
  travelTime: "7 YEARS"
}])
</script>
<template>
  <div class="containerA">
    <div class="inner-container">
      <div class="h-58px title-position">
        <span class="text-rwd barlow-text font-bold tracking-4.72px text-[rgba(255,255,255,0.25)] mr-24px">01</span>
        <span class="text-rwd barlow-text text-white tracking-4px">PICK YOUR DESTINATION</span>
      </div>
      <div class="relative w-100% aspect-ratio-[1110/734]">
        <transition name="wade">
          <div
            class="flex-1 flex absolute md:top-50% md:flex-row flex-col md:transform-translate-y-[-50%] md:mt-0 mt-42px md:text-start text-center items-center md:items-unset"
            :key="currentTarget">
            <div class="w-50% pic-rwd flex justify-center items-center mb-70px">
              <div class="w-89% aspect-ratio-square"><img :src="planet[currentTarget - 1].img" class="w-100% h-100%"
                  alt="">
              </div>
            </div>
            <div class="md:w-50% w-100% flex justify-center items-center">
              <div class="w-82.56% aspect-ratio-[445/468]  flex flex-col menu-rwd">
                <div class="h-29px flex mb-8.5% no-transition xs-position">
                  <div v-for="item of planet" :key="item.id" @click="() => currentTarget = item.id"
                    class="barlow-text xl:text-16px text-12px tracking-2px text-[#D0D6F9] xs-mr mr-26px xl:mr-32px cursor-pointer h-100% border-0 border-solid border-b-3px border-transparent"
                    :class="TargetClass(item.id)">
                    {{
                      item.name.toUpperCase() }}</div>
                </div>
                <div class="h-23.5% text-white bellefair-text title-rwd md:mb-16px mb-30px">{{
                  planet[currentTarget -
                    1].name.toUpperCase() }}
                </div>
                <div class="flex flex-col justify-between flex-1 article-rwd">
                  <div
                    class="xl:text-18px text-16px text-[#D0D6F9] barlow-text line-height-[180%] w-150% md:w-100% md:flex-none flex ml-[-25%] md:ml-0 md:mb-0">
                    {{
                      planet[currentTarget -
                        1].description }}</div>
                  <div>
                    <hr class="w-150% md:w-100% ml-[-25%] md:ml-0 mb-15px md:mb-0">
                  </div>

                  <div class="flex text-white justify-between w-150% md:w-100% ml-[-25%] md:ml-0 footer-rwd">
                    <div class="w-47.19% aspect-ratio-[210.5/61] flex flex-col justify-between xs-mb-24px">
                      <div class="text-[#D0D6F9] text-14px barlow-text xl:tracking-2px tracking-0 ">AVG. DISTANCE
                      </div>
                      <div class="bellefair-text xl:text-28px text-20px">{{
                        planet[currentTarget -
                          1].distance }}</div>
                    </div>
                    <div class="w-47.19% aspect-ratio-[210.5/61] flex flex-col justify-between">
                      <div class="text-[#D0D6F9] text-14px barlow-text xl:tracking-2px tracking-0">EST. TRAVEL TIME
                      </div>
                      <div class="bellefair-text xl:text-28px text-20px">{{
                        planet[currentTarget -
                          1].travelTime }}</div>
                    </div>
                  </div>
                </div>

              </div>
            </div>
          </div>
        </transition>
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

.inner-container {
  width: 100%;
  height: 792px;
  display: flex;
  flex-direction: column;
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

.title-position {
  text-align: start;
}

.text-rwd {
  font-size: 28px;
}

.title-rwd {
  font-size: 96px;
}

/* 平板版 (376px - 768px) */
@media (min-width: 377px) and (max-width: 768px) {
  .text-rwd {
    font-size: 20px;
  }

  .menu-rwd {
    align-items: center;
  }

  .pic-rwd {
    width: 60% !important;
  }

  .xs-mr {
    margin-right: 0 !important;
  }

  .xs-position {
    justify-content: space-between;
    width: 60%;
  }

  .article-rwd {
    width: 70%;
  }

  .title-rwd {
    font-size: 80px;
  }
}

/* 手機版 (375px 以下) */
@media (max-width: 376px) {

  .title-position {
    text-align: center;
  }

  .text-rwd {
    font-size: 16px;
  }

  .menu-rwd {
    align-items: center;
  }

  .xs-mr {
    margin-right: 0 !important;
  }

  .xs-position {
    justify-content: space-between;
    width: 100%;
  }

  .title-rwd {
    font-size: 56px;
  }

  .footer-rwd {
    flex-direction: column;
    align-items: center;
  }

  .xs-mb-24px {
    margin-bottom: 24px;
  }

  .article-rwd {
    width: 90%;
  }
}
</style>
