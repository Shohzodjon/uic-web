<template>
  <div>
    <swiper
      :breakpoints="{
        375: {
          slidesPerView: 2.5,
          spaceBetween: 8,
          grid: {
            rows: 2,
          },
        },
        576: {
          slidesPerView: 3,
          spaceBetween: 15,
          grid: {
            rows: 2,
          },
        },
        768: {
          slidesPerView: 4,
          spaceBetween: 15,
          grid: {
            rows: 2,
            col: 1,
          },
        },
        992: {
          slidesPerView: 5,
          spaceBetween: 20,
        },
      }"
      :grid="{
        rows: 1,
      }"
      :loop="true"
      :modules="modules"
      :pagination="{
        clickable: true,
      }"
    >
      <swiper-slide v-for="(item, index) in sliderCard" :key="index">
        <PartnerCard
          class="xs:w-[136px] lg:!w-full"
          v-bind="{ link: item?.company_site, image: item?.photo_url }"
        />
      </swiper-slide>
      <div class="mb-[64px]"></div>
    </swiper>
  </div>
</template>

<script lang="ts" setup>
import { Grid, Pagination } from "swiper";
import { Swiper, SwiperSlide } from "swiper/vue";
import PartnerCard from "@/stories/PartnerCard/PartnerCard.vue";
import "swiper/css";
import "swiper/css/grid";
import "swiper/css/pagination";

export interface Props {
  img: string;
  sliderCard: Array<object>;
}

const props = withDefaults(defineProps<Props>(), {
  img: "https://picsum.photos/id/1/200",
});

const modules = [Pagination, Grid];
</script>

<style>
.swiper-grid-column > .swiper-wrapper {
  flex-direction: row;
  align-items: flex-end;
}
</style>
