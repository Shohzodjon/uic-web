<template>
  <div class="mt-10">
    <h4 class="about__title mb-4" data-aos="fade-up" data-aos-duration="800">
      UIC Clan
    </h4>
    <i18n-t
      data-aos="fade-up"
      data-aos-duration="800"
      keypath="about_page.uic_clan_text"
      tag="p"
      scope="global"
      class="about_text mb-20"
      ><template v-slot:action>
        <a
          href="https://www.youtube.com/watch?v=mFybAaWBwqo"
          target="_blank"
          class="text-[#00A795] hover:text-[#00a79587] duration-300"
          >{{ $t("about_page.uic_clan_text_link") }}</a
        >
      </template>
    </i18n-t>
    <div
      class="relative bg-[#252527] p-4 sm:p-6 md:p-8 !pt-[80px] md:pt-[116px] border-[#37373A] border-[1px] rounded-[24px] grid sm:grid-cols-2 gap-6"
    >
      <img
        src="/uic-images/image/uic_clan.png"
        alt="uic clan logo"
        class="absolute top-0 left-[50%] translate-x-[-50%] translate-y-[-50%]"
      />
      <div
        data-aos="fade-left"
        data-aos-duration="800"
        v-for="(item, index) in imgs"
        @click="showImg(index, item)"
        :key="index"
        class="border-[transparent] border-[1px] rounded-[10px] duration-300 hover:border-[#00A795] hover:translate-y-[-5px] cursor-pointer"
      >
        <img :src="item" alt="uic clan" class="w-[100%]" />
      </div>
    </div>
    <vue-easy-lightbox
      :imgs="imgs"
      :index="index"
      :visible="visible"
      @hide="handleHide"
      :maxZoom="2"
      :moveDisabled="false"
    >
      <template v-slot:prev-btn="{ prev }">
        <button @click="prev" class="lightbox--prev">
          <UIcons name="lightbox_arrow_right" />
        </button>
      </template>
      <template v-slot:next-btn="{ next }">
        <button @click="next" class="lightbox--next">
          <UIcons name="lightbox_arrow_left" />
        </button>
      </template>
    </vue-easy-lightbox>
  </div>
</template>

<script setup lang="ts">
import UIcons from "@/stories/ui/UIcons/UIcons.vue";
// LIGHTBOX
import { ref } from "vue";

const hoverVisible = ref(false);
const visible = ref(false);
const index = ref();
const showImg = (i: number) => {
  index.value = i;
  visible.value = true;
};
const handleHide = () => {
  visible.value = false;
};
const imgs = [
  "/uic-images/image/uic_clan1.png",
  "/uic-images/image/uic_clan2.png",
  "/uic-images/image/uic_clan3.png",
  "/uic-images/image/uic_clan4.png",
];
</script>
