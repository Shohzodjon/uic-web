<template>
  <div
    class="text-white cursor-pointer bg-vacancy-card-background lg:py-10 md:py-9 md:px-11 py-7 px-9 lg:px-12 rounded-8"
  >
    <h1
      class="font-bold sm:text-2xl text-lg md:text-3xl lg:text-[40px] leading-120"
    >
      {{ vacancyId.title }}
    </h1>
    <hr class="my-4 lg:my-6 md:my-5 border-vacancy-card-divider" />
    <div class="flex flex-wrap gap-6 lg:gap-12 md:gap-10">
      <div class="hidden gap-4 sm:flex">
        <ShareNetwork
          class="tg newsSingleBlock__link"
          network="facebook"
          :url="`https://uic.group/vacancy/${vacancyId.id}`"
          :title="vacancyId.title"
        >
          <u-icons
            class="group hover:hover:text-[#00A795] text-[#AAAAAB] transition duration-300"
            name="vacancy_facebook"
          /> </ShareNetwork
        ><ShareNetwork
          class="tg newsSingleBlock__link"
          network="twitter"
          :url="`https://uic.group/vacancy/${vacancyId.id}`"
          :title="vacancyId.title"
        >
          <u-icons
            class="group hover:hover:text-[#00A795] text-[#AAAAAB] transition duration-300"
            name="vacancy_twitter"
          /> </ShareNetwork
        ><ShareNetwork
          class="tg newsSingleBlock__link"
          network="Telegram"
          :url="`https://uic.group/vacancy/${vacancyId.id}`"
          :title="vacancyId.title"
        >
          <u-icons
            class="group hover:hover:text-[#00A795] text-[#AAAAAB] transition duration-300"
            name="vacancy_telegram"
          />
        </ShareNetwork>
        <!--        <u-icons-->
        <!--          class="group hover:hover:text-[#00A795] text-[#AAAAAB] transition duration-300"-->
        <!--          name="vacancy_facebook"-->
        <!--        />-->
        <!--        <u-icons-->
        <!--          class="group hover:hover:text-[#00A795] text-[#AAAAAB] transition duration-300"-->
        <!--          name="vacancy_twitter"-->
        <!--        />-->
        <!--        <u-icons-->
        <!--          class="group hover:hover:text-[#00A795] text-[#AAAAAB] transition duration-300"-->
        <!--          name="vacancy_telegram"-->
        <!--        />-->
      </div>
      <div class="flex items-center gap-6">
        <div class="flex items-center gap-3">
          <span
            class="w-[32px] h-[32px] rounded-[50%] bg-[#ffffff24] flex items-center justify-center"
          >
            <u-icons class="text-white" name="date" />
          </span>
          <p
            v-if="vacancyId.date"
            class="lg:text-base text-xs md:text-sm text-vacancy-card-icon-text leading-5 font-['Roboto']"
          >
            {{ formatDate(vacancyId.date, true) }}
          </p>
        </div>
        <div class="flex items-center gap-3">
          <span
            class="w-[32px] h-[32px] rounded-[50%] bg-[#ffffff24] flex items-center justify-center"
          >
            <u-icons class="text-white" name="time" />
          </span>
          <p
            class="lg:text-base text-xs md:text-sm text-vacancy-card-icon-text leading-5 font-['Roboto']"
          >
            {{ vacancyId.time }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import UIcons from "@/stories/ui/UIcons/UIcons.vue";

export interface Props {
  title: string;
  workDay: string;
  workTime: string;
  vacancyId: Array;
}

withDefaults(defineProps<Props>(), {
  title: "",
  workDay: "",
  workTime: "",
});
</script>

<style scoped>
.icon-bg svg {
  width: 22.15px;
  height: 22.15px;
}
</style>
