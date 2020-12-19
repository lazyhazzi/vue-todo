<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <button class="addContainer" v-on:click="addTodo">
      <i class="fas fa-plus addBtn"></i>
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: ""
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoItem !== "") {
        const text = this.newTodoItem.trim();
        this.$store.commit("addOneItem", text);
        this.clearInput();
      } else {
        alert("할 일을 적어주세요.");
      }
    },
    clearInput() {
      this.newTodoItem = "";
    }
  }
};
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  display: flex;
  justify-content: space-between;
  height: 50px;
  min-height: 50px;
  border-radius: 5px;
  overflow: hidden;
}
.inputBox input {
  flex-grow: 1;
  padding: 0 0.8rem;
  border: none;
  font-size: 0.9rem;
}
.addContainer {
  width: 3rem;
  background: linear-gradient(to right, #6478fb, #8763fb);
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: #fff;
  vertical-align: middle;
}
</style>
