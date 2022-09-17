<template>
  <div class="max-w-[990px] mx-auto">
    <img
      data-aos="zoom-in"
      data-aos-duration="1000"
      src="/uic-images/image/uic_about.png"
      alt="UIC logo"
      class="mx-auto my-[88px]"
    />
    <div>
      <h4
        class="mb-2 md:mb-4 about__title"
        data-aos="fade-up"
        data-aos-duration="900"
      >
        {{ $t("about_page.about") }}
      </h4>
      <div class="about_text" data-aos="fade-up" data-aos-duration="900">
        <p class="mb-3">
          {{ $t("about_page.about_uic") }}
        </p>
        <p>
          {{ $t("about_page.about_uic2") }}
        </p>
      </div>
    </div>
    <div data-aos="fade-up" data-aos-duration="700">
      <div
        @click="showreelModal"
        class="showrell-box bg-[#252527] border-[#00A795] hover border-dashed rounded-[12px] border-[1px] p-6 flex items-center justify-center flex-col md:flex-row gap-y-8 mt-10 cursor-pointer"
      >
        <div
          class="!scale-90 w-[94px] h-[94px] scale-125 opacity-90 relative flex justify-center showreel-wrapper text-[#fff] mr-7"
        >
          <u-icons
            class="absolute z-10 flex items-center justify-center rotate-anim"
            name="showreel"
          />
          <u-icons
            class="flex items-center justify-center left-[50%]"
            name="showreel_play"
          />
        </div>
        <div class="inline">
          <p
            class="mr-2 font-['Roboto'] font-medium leading-[144%] inline text-[14px] md:"
          >
            {{ $t("about_page.about_uic_showreel") }}
          </p>
          <u-icons name="arrow_right_small" class="inline translate-y-[3px]" />
        </div>
      </div>
    </div>

    <!--    SHOWREEL MODAL-->
    <transition name="fade">
      <div class="overlay" :class="[showModal ? 'active_modal' : '']">
        <div class="flex items-center justify-center w-full h-full relative">
          <button
            class="text-white absolute top-[5%] right-[5%] text-base"
            @click="showreelModal"
          >
            <u-icons name="close_icon" class="close--icon" />
          </button>
          <div class="w-[95%] sm:w-[85%] h-[300px] sm:h-[400px] lg:h-[600px]">
            <transition name="fade">
              <iframe
                v-if="showModal"
                width="100%"
                height="100%"
                src="https://www.youtube.com/embed/1vx_W6o_t68"
                title="YouTube video player"
                frameborder="0"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                allowfullscreen
              ></iframe>
            </transition>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import UIcons from "@/stories/ui/UIcons/UIcons.vue";
import { ref } from "vue";
let showModal = ref(false);
function showreelModal() {
  showModal.value = !showModal.value;
  if (showModal.value) {
    document.body.style.overflow = "hidden";
  } else {
    document.body.style.overflow = "auto";
  }
}
</script>

<style scoped>
.showrell-box {
  transition: 0.3s ease-in-out;
}
.showrell-box:hover {
  box-shadow: 0 0 52px -16px rgba(0, 167, 149, 0.36);
  /*transform: translateY(-3px);*/
}
.overlay {
  width: 100vw;
  height: 100vh;
  z-index: 999999 !important;
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(1px);
  position: fixed;
  transition: all 0.5s linear;
  left: 0;
  opacity: 1;
  left: 0;
  top: 0;
  transform: scale(0.2);
  bottom: 0;
  display: none;
  z-index: 999999999 !important;
}
.active_modal {
  opacity: 1;
  transform: scale(1);
  display: block;
}
@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.rotate-anim {
  animation: rotate 7s linear infinite;
}
</style>
