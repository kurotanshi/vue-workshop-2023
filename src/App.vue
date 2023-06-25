<script setup>
import { ref } from "vue";

const toggle = ref(false);
</script>

<template>
  <div
    class="bg-emerald-700 h-[100vh] w-full block overflow-x-auto overflow-y-hidden"
  >
    <div id="board-wrapper" class="h-full w-full p-4 block overflow-auto">
      <div class="flex flex-row items-start">
        <!-- card -->
        <div
          v-for="i in 3"
          :key="i"
          @click="toggle = !toggle"
          class="border rounded-sm bg-slate-200 border-gray-500 mx-2 min-w-[300px] p-2 block"
        >
          <!-- column -->
          <div class="text-ellipsis text-lg w-4/5 block overflow-hidden">
            標題
          </div>
          <!-- <textarea class="border-none h-8 w-full p-1 resize-none overflow-hidden block"></textarea> -->

          <!-- tasks -->
          <div
            class="bg-white my-2 w-full py-2 px-3 block overflow-hidden select-none"
          >
            <div class="font-bold block">卡片標題</div>
            <div class="text-ellipsis overflow-hidden">卡片內容</div>
          </div>

          <div
            class="bg-white my-2 w-full py-2 px-3 block overflow-hidden select-none"
          >
            <div class="font-bold block">卡片標題</div>
            <div class="text-ellipsis overflow-hidden">卡片內容</div>
          </div>
          <!-- tasks -->

          <!-- add new task -->
          <div class="my-3">
            <div
              class="cursor-pointer bg-slate-200 p-2 text-slate-500 hover:bg-slate-300"
            >
              + 點擊以新增任務
            </div>
            <!-- <textarea class="h-10 w-full p-2 block resize-none" placeholder="為這張卡片輸入標題"></textarea> -->
          </div>
          <!-- add new task -->
        </div>
        <!-- card -->

        <!-- add new card -->
        <div
          class="border rounded-sm cursor-pointer bg-slate-200 bg-opacity-70 border-gray-500 mx-2 min-w-[300px] p-2 w-[300px] block hover:bg-opacity-90"
        >
          <div class="block select-none">+ 新增其他列表</div>
          <!-- <div>
            <input type="text" ref="target" placeholder="為列表輸入標題" class="w-full p-2 block" />
          </div> -->
        </div>
        <!-- add new card -->
      </div>
    </div>

    <!-- lightbox -->
    <div
      v-if="toggle"
      class="h-full bg-slate-800 bg-opacity-70 w-full top-0 left-0 z-100 fixed"
    >
      <div
        class="bg-white h-auto mx-auto py-8 px-12 top-[15vh] w-1/2 block relative"
      >
        <div>
          <input
            ref="target"
            type="text"
            class="border text-xl mb-6 w-full p-2"
          />
        </div>

        <textarea
          class="border h-[300px] w-full p-3 overflow-x-hidden overflow-y-auto resize-none"
        ></textarea>

        <div class="mt-4 text-right">
          <button
            class="border bg-rose-500 text-white mr-6 py-2 px-4 hover:bg-rose-700"
          >
            刪除
          </button>
          <button
            class="border bg-slate-200 py-2 px-4 hover:bg-slate-400 hover:text-slate-100"
          >
            儲存送出
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
