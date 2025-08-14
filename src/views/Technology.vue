<script setup>
import { onMounted, ref } from 'vue';

const totalPage = ref([{ id: 1, title: 'LAUNCH VEHICLE', detail: "A launch vehicle or carrier rocket is a rocket-propelled vehicle used to carry a payload from Earth's surface to space, usually to Earth orbit or beyond. Our WEB-X carrier rocket is the most powerful in operation. Standing 150 metres tall, it's quite an awe-inspiring sight on the launch pad!", pic: './src/assets/technology/image-launch-vehicle-portrait.jpg' },
{ id: 2, title: 'SPACEPORT', detail: "A spaceport or cosmodrome is a site for launching (or receiving) spacecraft, by analogy to the seaport for ships or airport for aircraft. Based in the famous Cape Canaveral, our spaceport is ideally situated to take advantage of the Earth’s rotation for launch.", pic: './src/assets/technology/image-spaceport-portrait.jpg' },
{ id: 3, title: 'SPACE CAPSULE', detail: "A space capsule is an often-crewed spacecraft that uses a blunt-body reentry capsule to reenter the Earth's atmosphere without wings. Our capsule is where you'll spend your time during the flight. It includes a space gym, cinema, and plenty of other activities to keep you entertained.", pic: './src/assets/technology/image-space-capsule-portrait.jpg' }]);
const currentPage = ref(1);
const pics = ref([{ id: 1, pic: "/src/assets/technology/image-launch-vehicle-landscape.jpg" }, { id: 2, pic: "/src/assets/technology/image-spaceport-landscape.jpg" }, { id: 3, pic: "/src/assets/technology/image-space-capsule-landscape.jpg" }])
</script>
<template>
  <div class="containerA">
    <div class="mb-24px span-container">
      <span
        class="span-text-rwd barlow-text font-bold tracking-4.72px text-[rgba(255,255,255,0.25)] mr-24px">03</span><span
        class="span-text-rwd barlow-text text-white tracking-4px">SPACE LAUNCH 101</span>
    </div>
    <div class="w-100% h-734px md:flex flex-none md:pos-unset absolute left-0">
      <div class="md:hidden block mb-30px">
        <img :src="pics[currentPage - 1].pic" alt="" width="100%">
      </div>
      <div class="md:w-48.559% w-100% md:py-215px py-0 box-border">
        <div class="w-100% h-100% md:flex flex-none">
          <div
            class="flex md:flex-col flex-row justify-between md:w-fit w-100% box-border px-35% xs-px md:px-0 mb-40px md:mb-0">
            <div v-for="item in totalPage"
              class="md:w-80px xs-w-40 w-56px md:h-80px h-56px rounded-100% border-1px border-solid border-[rgba(255,255,255,0.25)] text-white text-center content-center cursor-pointer md:text-32px text-24px bellefair-text transition-700"
              :class="currentPage === item.id ? 'bg-white !text-[#0B0D17]' : 'hover-border-white'"
              @click="currentPage = item.id">
              {{ item.id }}
            </div>
          </div>
          <div class="w-10.078%"></div>
          <div class="flex-1 relative">
            <Transition name="wade">
              <div :key="currentPage" class="absolute h-100% flex flex-col md:justify-between justify-unset">
                <div class="text-[rgba(255,255,255,0.5042)] bellefair-text tn-text mb-16px text-center md:text-start">
                  THE
                  TERMINOLOGY…</div>
                <div class="bellefair-text text-white title-text  mb-24px text-center md:text-start">{{
                  totalPage[currentPage - 1].title
                }}</div>
                <div
                  class="barlow-text md:text-18px text-16px line-height-[180%] text-[#D0D6F9] text-center md:text-start box-border px-20% md:px-0">
                  {{
                    totalPage[currentPage -
                      1].detail
                  }}
                </div>
              </div>
            </Transition>
          </div>

        </div>
      </div>
      <div class="w-2.882%"></div>
      <div class="w-48.559% py-67px box-border">
        <div class="w-100% h-100% relative">
          <Transition name="wade">
            <img :src="totalPage[currentPage - 1].pic" alt="" height="100%" width="100%" :key="currentPage"
              class="absolute">
          </Transition>
        </div>
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
  padding-right: 0;
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

.span-text-rwd {
  font-size: 28px;
}

.tn-text {
  font-size: 32px;
}

.title-text {
  font-size: 56px;
}

@media (min-width: 377px) and (max-width: 768px) {
  .containerA {
    padding: 48px 5.45%;
  }

  .span-container {
    margin-bottom: 80px;
  }

  .span-text-rwd {
    font-size: 20px;
  }

  .tn-text {
    font-size: 24px;
  }

  .title-text {
    font-size: 40px;
  }
}

@media (max-width: 376px) {
  .containerA {
    padding: 48px 10.45%;
  }

  .span-container {
    margin-bottom: 80px;
    text-align: center;
  }

  .span-text-rwd {
    font-size: 16px;
  }

  .xs-px {
    padding: 0 25%;
  }

  .xs-w-40 {
    width: 40px;
    height: 40px;
    box-sizing: border-box;
    font-size: 18px;
  }

  .tn-text {
    font-size: 18px;
  }

  .title-text {
    font-size: 24px;
  }
}
</style>
