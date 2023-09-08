<script setup>
import { ref } from "vue";
import { useFocus } from "@vueuse/core";
import { vOnClickOutside } from "@vueuse/components";
import { useStore } from "/src/stores";

const store = useStore();
const { addNewCard } = store;

const target = ref();
useFocus(target, { initialValue: true });

const isEditing = ref(false);
const title = ref("");

const addCard = () => {
  addNewCard(title.value);
  title.value = "";
  isEditing.value = false;
};
</script>

<template>
  <div class="new-card">
    <div @click="isEditing = true" v-if="!isEditing" class="block select-none">
      + 新增其他列表
    </div>
    <div v-else>
      <input
        type="text"
        ref="target"
        v-on-click-outside="() => (isEditing = false)"
        @keydown.enter="addCard"
        placeholder="為列表輸入標題"
        class="w-full p-2 block"
        v-model="title"
      />
    </div>
  </div>
</template>

<style scoped>
.new-card {
  @apply border rounded-sm cursor-pointer bg-slate-200 bg-opacity-70 border-gray-500 mx-2 min-w-[300px] p-2 w-[300px] block hover:bg-opacity-90;
}
</style>
