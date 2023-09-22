<template>
  <section class="m-auto">
    <h1 class="text-center m-4 font-extrabold text-5xl text-cyan-500">
      Todo List
    </h1>
    <div class="w-96 h-96">
      <div
        v-for="(item, index) in savedInput"
        :key="index"
        class="flex justify-between py-4 px-6 border-b"
      >
      <p class="text-gray-700 font-semibold text-base">
        {{ item }}
        </p>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6 cursor-pointer hover:text-red-500"
          @click="deleteItem(index)"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M14.74 9l-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 01-2.244 2.077H8.084a2.25 2.25 0 01-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 00-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 013.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 00-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 00-7.5 0"
          />
        </svg>
      </div>
      <button
        class="m-auto cursor-pointer my-3 w-32 h-12 rounded-2xl bg-purple-500 text-purple-50 flex items-center justify-center text-base font-normal"
        @click="addNewTask"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M12 4.5v15m7.5-7.5h-15"
          />
        </svg>
        New Task
      </button>
      <AddTask v-if="showAddTask" @close="close" @save="submitTask" />
    </div>
  </section>
</template>
<script setup>
import AddTask from "./AddTask.vue";
</script>
<script>
export default {
  data() {
    return {
      showAddTask: false,
      savedInput: [],
      deleteText: false,
    };
  },
  methods: {
    addNewTask() {
      this.showAddTask = true;
    },
    close() {
      this.showAddTask = false;
    },
    submitTask(input) {
      this.savedInput.push(input);
      console.log(this.savedInput);
      this.showAddTask = false;
    },
    deleteItem(ele){
        this.savedInput.splice(ele,1);
    },
  },
};
</script>
