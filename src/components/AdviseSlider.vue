<template>
  <div class="advise-section">
    <div class="flex flex-col items-center justify-center">
      <h6 class="mb-2 text-center uppercase section-title_green">
        {{ $t("advise_view") }}
      </h6>
      <h3 class="text-center section-title_white mb-18">{{ $t("advise") }}</h3>
    </div>
    <div class="advise-slider md:mt-16 mt-8">
      <swiper
        :modules="modules"
        centeredSlides="true"
        :spaceBetween="20"
        :loop="true"
        v-bind="settings"
      >
        <!-- v-bind="settings" -->
        <swiper-slide
          v-for="(item, index) in props.recommendation"
          :key="index"
          class="slug--slider"
        >
          <blog-card
            class="w-full h-[210px] slug--card"
            :title="item.title"
            :text="item.description"
            :img="item.image_url"
            alt="blogs-image"
            :date="item.date"
            :views="item.views"
            :type="item.category.category"
            :slug="`${item.id}`"
            @click="giveParam(item.id)"
          />
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>
<script setup lang="ts">
import { onMounted } from "vue";
import "swiper/css";
import "swiper/css/pagination";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Pagination } from "swiper";
import BlogCard from "@/stories/common/cards/BlogCard/BlogCard.vue";
import router from "@/router";
import { useBlogStore } from "@/stores/blog";

const eachBlog = useBlogStore();
function giveParam(par) {
  eachBlog.fetchEachBlog(par);
  window.scrollTo(0, 0);
}

onMounted(() => {
  eachBlog.fetchEachBlog(router.currentRoute._rawValue.params.slug);
});
const props = defineProps({
  recommendation: Object,
});

const modules = [Pagination, Autoplay];
const settings = {
  loop: true,
  centeredSlides: true,
  loopFillGroupWithBlank: true,
  autoplay: {
    delay: 2500,
    disableOnInteraction: false,
  },
  "grab-cursor": true,
  breakpoints: {
    300: {
      slidesPerView: 1,
      spaceBetween: 44,
    },
    500: {
      slidesPerView: 1,
      spaceBetween: 44,
    },
    900: {
      slidesPerView: 2,
      spaceBetween: 44,
    },
    1200: {
      slidesPerView: 4,
      spaceBetween: 44,
    },
  },
};
</script>
<style scoped>
.advise-slider .swiper {
  padding-top: 20px;
  width: 100%;
}

@media (max-width: 575px) {
  .advise-slider .swiper {
    padding-top: 75px !important;
  }
}

.advise-section .section-title_green {
  position: relative;
}

.advise-section .section-title_green:before {
  content: "";
  position: absolute;
  left: -47px;
  top: 8px;
  width: 32px;
  height: 2px;
  background-color: #ffffff;
  opacity: 0.2;
}

.advise-section .section-title_green:after {
  content: "";
  position: absolute;
  right: -47px;
  top: 8px;
  width: 32px;
  height: 2px;
  background-color: #ffffff;
  opacity: 0.2;
}
</style>
<style>
.slug--slider {
  width: 562px !important;
}
.slug--card > div {
  width: 562px;
}
@media screen and (min-width: 370px) and (max-width: 575.9px) {
  .slug--slider {
    width: 95% !important;
  }
  .slug--card > div {
    width: 100% !important;
  }
}
</style>
