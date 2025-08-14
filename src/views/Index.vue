<script setup></script>
<template>
  <div class="text-white">
    <div class="inner-page">
      <div class="inner-content md:flex flex-none items-center">
        <div class="md:w-540px w-100%">
          <div
            class="barlow-text xs-text-16px tracking-[2px] md:tracking-4px mb-24px text-[#D0D6F9] md:mt-0 mt-128px md:text-start text-center">
            SO, YOU
            WANT TO TRAVEL TO</div>
          <div class="bellefair-text text-80px md:text-144px md:text-start text-center">SPACE</div>
          <div
            class="barlow-text md:text-22px text-15px text-[#D0D6F9] line-height-[180%] text-start tracking-0px md:px-0 px-128px xs-px md:pb-0 pb-66px">
            Let’s face it;
            if you want to
            go to
            space, you might as well
            genuinely go
            to outer
            space and not hover
            kind of on the edge of it. Well sit back, and relax because we’ll give you a truly out of this world
            experience!</div>
        </div>
        <div class="flex-1 flex items-center md:justify-end justify-center">
          <RouterLink to="/destination" class="decoration-none">
            <div id="explore"
              class="text-center content-center text-black bellefair-text text-32px w-272px h-272px  bg-white rounded-100%">
              EXPLORE
            </div>
          </RouterLink>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
@media (min-width: 769px) {
  .inner-page {
    width: 1110px;
    height: 632px;
    margin: 128px auto;
    display: flex;
    align-items: end;
  }

  .xs-text-16px {
    font-size: 28px;
  }

  .inner-content {
    width: 100%;
    height: 343px;
  }

  #explore {
    transition: 0.4s;
    outline: 88px solid transparent;
    cursor: pointer;
  }

  #explore:hover {
    outline: 88px solid rgba(255, 255, 255, 0.1);
    color: rgba(11, 13, 23, 0.5);
  }
}

@media (max-width: 768px) {

  /* 平板範圍 */
  .inner-page {
    width: 100%;
    margin: 0;
    display: block;
  }

  .xs-text-16px {
    font-size: 28px;
  }

  .xs-px {
    padding: 0 20%;
    padding-bottom: 60px;
  }

}

@media screen and (max-width: 376px) {
  .xs-text-16px {
    font-size: 16px;
  }

  .xs-px {
    padding: 0 30px;
    padding-bottom: 60px;
  }
}
</style>
