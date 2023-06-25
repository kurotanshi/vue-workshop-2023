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
          class="bg-slate-200 block border rounded-sm p-2 mx-2 border-gray-500 min-w-[300px]"
        >
          <!-- column -->
          <div class="block overflow-hidden text-ellipsis w-4/5 text-lg">
            標題
          </div>
          <!-- <textarea class="resize-none overflow-hidden border-none w-full p-1 h-8 block"></textarea> -->

          <!-- tasks -->
          <div
            class="block my-2 w-full py-2 px-3 bg-white overflow-hidden select-none"
          >
            <div class="block font-bold">卡片標題</div>
            <div class="overflow-hidden text-ellipsis">卡片內容</div>
          </div>

          <div
            class="block my-2 w-full py-2 px-3 bg-white overflow-hidden select-none"
          >
            <div class="block font-bold">卡片標題</div>
            <div class="overflow-hidden text-ellipsis">卡片內容</div>
          </div>
          <!-- tasks -->

          <!-- add new task -->
          <div class="my-3">
            <div
              class="bg-slate-200 p-2 hover:bg-slate-300 cursor-pointer text-slate-500"
            >
              + 點擊以新增任務
            </div>
            <!-- <textarea class="block w-full resize-none p-2 h-10" placeholder="為這張卡片輸入標題"></textarea> -->
          </div>
          <!-- add new task -->
        </div>
        <!-- card -->

        <!-- add new card -->
        <div
          class="bg-slate-200 block border rounded-sm p-2 mx-2 border-gray-500 w-[300px] cursor-pointer bg-opacity-70 hover:bg-opacity-90 min-w-[300px]"
        >
          <div class="block select-none">+ 新增其他列表</div>
          <!-- <div>
            <input type="text" ref="target" placeholder="為列表輸入標題" class="block w-full p-2" />
          </div> -->
        </div>
        <!-- add new card -->
      </div>
    </div>

    <!-- lightbox -->
    <div
      v-if="toggle"
      class="fixed top-0 left-0 w-full h-full bg-slate-800 z-100 bg-opacity-70"
    >
      <div
        class="w-1/2 h-auto block relative mx-auto top-[15vh] bg-white py-8 px-12"
      >
        <div>
          <input
            ref="target"
            type="text"
            class="w-full p-2 text-xl border mb-6"
          />
        </div>

        <textarea
          class="w-full h-[300px] p-3 overflow-x-hidden overflow-y-auto resize-none border"
        ></textarea>

        <div class="text-right mt-4">
          <button
            class="border bg-rose-500 text-white py-2 px-4 hover:bg-rose-700 mr-6"
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
