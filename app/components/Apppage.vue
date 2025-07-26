<template>
  <div class="w-full max-w-6xl mx-auto px-4 py-6 bg-slate-200">
    <div class="flex justify-end mb-4">
      <button @click="toggleView" class="flex">
        {{ showAll ? "Xem tất cả" : "Thu gọn" }}
        <img :src="showAll ? '/img/turnup.png' : '/img/turnright.png'" alt="" />
      </button>
    </div>

    <div v-if="!showAll" class="flex items-center justify-center gap-2">
      <button
        @click="prevSlide"
        class="bg-white shadow px-3 py-2 h-24 w-10 rounded-tl-xl rounded-bl-xl"
      >
        <img src="/img/left.png" alt="" class="w-5 h-2" />
      </button>

      <div class="overflow-hidden">
        <div
          class="flex transition-transform duration-500"
          :style="{
            transform: `translateX(-${currentIndex * (100 / cardsToShow)}%)`,
          }"
        >
          <div
            v-for="(card, index) in cards"
            :key="index"
            class="flex-shrink-0 w-[20%] px-2"
          >
            <div class="card bg-white shadow rounded p-2">
              <img :src="card.image" alt="" class="w-full h-auto rounded" />
            </div>
          </div>
        </div>
      </div>

      <button
        @click="nextSlide"
        class="bg-white shadow px-3 py-2 h-24 w-10 rounded-tr-xl rounded-br-xl"
      >
        <img src="/img/right.png" alt="" class="w-5 h-2" />
      </button>
    </div>

    <div v-else class="grid grid-cols-5 gap-4 mt-4">
      <div
        v-for="(card, index) in cards"
        :key="'all-' + index"
        class="card bg-white shadow rounded p-2"
      >
        <img :src="card.image" alt="" class="w-full h-auto rounded" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const cards = Array.from({ length: 10 }, (_, i) => ({
  image: `/img/Matchs-main.png`,
}));

const cardsToShow = 5;
const currentIndex = ref(0);
const showAll = ref(false);
const maxIndex = cards.length - cardsToShow;

function nextSlide() {
  if (currentIndex.value < maxIndex) currentIndex.value++;
}

function prevSlide() {
  if (currentIndex.value > 0) currentIndex.value--;
}

function toggleView() {
  showAll.value = !showAll.value;
}
</script>

<style scoped>
.card img {
  object-fit: cover;
  height: 160px;
}
</style>
