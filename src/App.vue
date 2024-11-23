<script setup lang="ts">
import { ref } from "vue";

const nowPage = ref(0);

const changeNowPage = () => {
  nowPage.value = nowPage.value + 1;
};

const getImageUrl = (name: any) => {
  return new URL(`/src/assets/images/${name}`, import.meta.url).href;
};

const pageData = [
  {
    title: "早安",
    titleJp: "おはよう",
    image: getImageUrl("2024-1.jpeg"),
    btn: "下一頁",
  },
  {
    title: "今天好像有人生日？",
    titleJp: "今日誕生日の人がいるみたいですね？",
    image: getImageUrl("2024-2.jpeg"),
    btn: "下一頁",
  },
  {
    title: "有些任務要進行，希望壽星可以順利完成❤️",
    titleJp: "実行すべきタスクがあります，無事に完成できるといいですね❤️",
    image: getImageUrl("2024-3.jpeg"),
    btn: "下一頁",
  },

  {
    title: "那就開始吧！",
    titleJp: "それでは始めましょう!",
    image: getImageUrl("2024-4.jpeg"),
    btn: "開始",
  },
];
</script>

<template>
  <div style="display: flex; justify-content: center; align-items: center">
    <div class="card" v-if="nowPage <= 3">
      <div class="title">
        <p class="title-tw">{{ pageData[nowPage].title }}</p>
        <p class="title-jp">{{ pageData[nowPage].titleJp }}</p>
      </div>

      <div class="img-area">
        <img :src="pageData[nowPage].image" alt="hi" />
      </div>

      <div class="btn-area">
        <el-button class="big-btn" type="warning" @click="changeNowPage">
          {{ pageData[nowPage].btn }}
        </el-button>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.card {
}
</style>
