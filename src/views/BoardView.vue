<script setup>
import { computed } from "vue";
import { useStore } from "/src/stores";
import draggable from "vuedraggable";

const store = useStore();
const list = computed(() => store.lists);
</script>

<template>
  <div
    class="bg-emerald-700 h-[100vh] w-full block overflow-x-auto overflow-y-hidden"
  >
    <div id="board-wrapper" class="h-full w-full p-4 block overflow-auto">
      <draggable
        :list="list"
        group="card"
        itemKey="id"
        ghost-class="opacity-30"
        class="flex flex-row items-start"
      >
        <!-- 原本的 Card -->
        <template #item="{ element }">
          <Card v-bind="element" />
        </template>

        <template #footer>
          <AddNewCard />
        </template>
      </draggable>
    </div>

    <!-- lightbox -->
    <router-view />
  </div>
</template>
