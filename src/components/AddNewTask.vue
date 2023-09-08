<script setup>
import { ref } from "vue";
import { useFocus } from "@vueuse/core";
import { vOnClickOutside } from "@vueuse/components";
import { useStore } from "/src/stores";

const props = defineProps({
  id: String,
});

const store = useStore();
const { addTask } = store;

const target = ref();
useFocus(target, { initialValue: true });

const newTitle = ref("");
const isEditing = ref(false);

const addTaskToCard = () => {
  addTask(props.id, newTitle.value);
  newTitle.value = "";
  isEditing.value = false;
};
</script>

<template>
  <div class="my-3">
    <div
      v-if="!isEditing"
      @click="isEditing = true"
      class="cursor-pointer bg-slate-200 p-2 text-slate-500 hover:bg-slate-300"
    >
      + 點擊以新增任務
    </div>
    <textarea
      v-else
      ref="target"
      v-on-click-outside="() => (isEditing = false)"
      v-model="newTitle"
      @keydown.enter="addTaskToCard"
      class="h-10 w-full p-2 block resize-none"
      placeholder="為這張卡片輸入標題"
    ></textarea>
  </div>
</template>
