<template>
  <div class="w-full h-28 bg-yellow-300 flex">
    <div class="w-96 h-28 bg-black rounded-tr-[40px] text-white">
      <p class="text-right me-4 text-8xl">LOGO</p>
    </div>

    <div class="flex flex-col justify-between flex-1">
      <div class="w-full h-12 bg-yellow-300 text-white">
        <div class="flex gap-10 text-black ms-2 mt-1">
          <div
            v-for="(button, index) in buttons"
            :key="index"
            class="relative inline-block text-left"
          >
            <button
              @click="toggleDropdown(index)"
              class="px-6 py-2 rounded-[20px] hover:bg-black hover:scale-110 transition-transform duration-300 hover:text-yellow-300"
            >
              {{ button.label }}
            </button>
            <div
              v-if="openIndex === index"
              class="absolute left-0 mt-2 w-40 bg-gray-400 rounded shadow-lg z-50"
            >
              <ul>
                <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                  <img src="/img/ball.png" class="me-2" />
                  BÓNG ĐÁ
                </li>
                <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                  <img src="/img/ballkid.png" class="me-2" />
                  Đua bi
                </li>
                <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                  <img src="/img/basketball.png" class="me-2" />
                  BÓNG rổ
                </li>
                <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                  <img src="/img/game.png" class="me-2" />
                  E-sports
                </li>
                <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                  <img src="/img/card.png" class="me-2" />
                  Casino
                </li>
              </ul>
            </div>
          </div>
          <div class="rounded-[20px] bg-black w-80 flex">
            <div class="relative">
              <div
                class="bg-white text-black rounded-[20px] w-40 flex items-center justify-between gap-2 px-2 mt-2 ms-3"
              >
                <button class="flex" @click="toggleBalance">
                  <img src="/img/Coin.png" alt="Coin" class="w-4 h-4 mt-1" />
                  <p class="ms-2">10000</p>
                  <img src="/img/icon_size.png" alt="Coin" class="w-10 h-6" />
                </button>
              </div>

              <div
                v-if="openbalance"
                class="absolute top-full left-0 mt-2 w-40 bg-gray-400 rounded shadow-lg z-50"
              >
                <ul>
                  <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                    <img src="/img/silvercoin.png" class="me-2" />
                    30.00
                  </li>
                  <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                    <img src="/img/kcoin.png" class="me-2" />
                    400.00
                  </li>
                </ul>
              </div>
            </div>

            <div class="w-40 flex items-center justify-start gap-2">
              <img src="/img/bell.png" alt="Bell" class="w-5 h-5" />
              <img src="/img/message.png" alt="Message" class="w-5 h-5" />
              <img src="/img/calender.png" alt="Calendar" class="w-5 h-5" />
            </div>
            <div class="relative me-3">
              <button @click="toggleProfile">
                <img src="/img/user.png" />
              </button>
              <div
                v-if="openprofile"
                class="absolute top-full left-0 mt-2 w-60 bg-gray-400 rounded shadow-lg z-50"
              >
                <ul>
                  <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                    <img src="/img/pf/pf.png" class="me-2" />
                    Trung tâm Tài khoản
                  </li>
                  <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                    <img src="/img/pf/home.png" class="me-2" />
                    Trang cá nhân
                  </li>
                  <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                    <img src="/img/pf/point.png" class="me-2" />
                    Nhiệm vụ
                  </li>
                  <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                    <img src="/img/pf/wallet.png" class="me-2" />
                    Ví của bạn
                  </li>
                  <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                    <img src="/img/pf/graph.png" class="me-2" />
                    Lịch sử giao dịch
                  </li>
                  <li class="px-4 py-2 hover:bg-gray-100 cursor-pointer flex">
                    <img src="/img/pf/out.png" class="me-2" />
                    Thoát tài khoản
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- section header 2 -->
      <div class="w-full h-12 bg-black text-white">
        <div class="w-full h-12 text-white flex">
          <div class="flex gap-10 text-black ms-2 mt-1">
            <div
              v-for="(button, index) in buttonunder"
              :key="index"
              class="relative inline-block text-left"
            >
              <button
                class="px-5 py-2 rounded-[20px] hover:scale-110 transition-transform duration-300 text-yellow-300 flex"
              >
                <img :src="`/img/${button.icon}`" class="me-2" />
                {{ button.label }}
              </button>
            </div>
          </div>
          <div class="ms-7 px-1 py-2 rounded-[20px] bg-black w-80 flex">
            <div
              class="bg-white text-black rounded-[20px] w-40 flex items-center justify-start gap-2 px-2"
            >
              <img src="/img/VN.png" alt="Coin" class="w-6 h-6" />
              <p>Tiếng việt</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const buttons = ref<{ label: string }[]>([
  { label: "lịch trực tiếp" },
  { label: "Lịch Thi Đấu" },
  { label: "Tỷ lệ kèo" },
  { label: "Kết quả" },
  { label: "Phòng chat" },
  { label: "Tin tức" },
]);
const buttonunder = ref<{ label: string; icon: string }[]>([
  { label: "Bảng Tin", icon: "sms.png" },
  { label: "Reels", icon: "reel.png" },
  { label: "Highlight", icon: "video.png" },
  { label: "Tip Kèo", icon: "star.png" },
  { label: "Phim Ảnh", icon: "film.png" },
  { label: "Truyện Tranh", icon: "book.png" },
]);

const openIndex = ref<number | null>(null);
const openbalance = ref(false);
const openprofile = ref(false);
function toggleDropdown(i: number) {
  openIndex.value = openIndex.value === i ? null : i;
}
function toggleBalance() {
  openbalance.value = !openbalance.value;
}
function toggleProfile() {
  openprofile.value = !openprofile.value;
}
</script>
