<template>
  <div class="modal-overlay">
    <div class="modal">
        <form @submit.prevent="submit" class="px-4 grid">
          <input
            type="text"
            placeholder="Enter Task"
            class="border p-2"
            v-model="inputData"
          />
          <div class="flex space-x-2 justify-end">
            <button>Save</button>
            <button @click="close">Cancel</button>
          </div>
        </form>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputData: null,
    };
  },
  methods: {
    close() {
      this.$emit("close");
    },
    submit() {
      this.$emit("save", this.inputData);
      console.log(this.inputData);
    },
  },
};
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  background-color: #000000da;
}

.modal {
  text-align: center;
  background-color: white;
  height: 200px;
  width: 380px;
  margin-top: 10%;
  padding: 60px 0;
  border-radius: 10px;
}

button {
  background-color: #00d2f6;
  width: 100px;
  height: 32px;
  color: white;
  font-size: 14px;
  border-radius: 5px;
  margin-top: 30px;
}
</style>
