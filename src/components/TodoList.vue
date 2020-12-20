<template>
  <div>
    <transition-group name="list" tag="ul">
      <li v-for="(todoItem, index) in this.todoItems" v-bind:key="todoItem.item" class="shadow">
        <button type="button" v-on:click="toggleComplete({todoItem, index})" class="checkBtn">
          <i class="fas fa-check" v-bind:class="{checkBtnCompleted: todoItem.completed}"></i>
        </button>
        <span v-bind:class="{textCompleted: todoItem.completed}">{{todoItem.item}}</span>
        <button type="button" v-on:click="removeTodo({todoItem, index})" class="removeBtn">
          <i class="fas fa-trash-alt"></i>
        </button>
      </li>
    </transition-group>
  </div>
</template>

<script>
import { mapGetters, mapMutations } from "vuex";

export default {
  methods: {
    ...mapMutations({
      removeTodo: "removeOneItem",
      toggleComplete: "toggleOneItem"
    })
  },
  computed: {
    ...mapGetters({ todoItems: "storedTodoItems" })
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  padding-left: 0;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  align-items: center;
  min-height: 50px;
  height: 50px;
  line-height: 42px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: #fff;
  border-radius: 5px;
}
.checkBtn {
  /* line-height: 45px; */
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.removeBtn {
  height: 100%;
  margin-left: auto;
  color: #de4343;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}

/* List Transition Effect */
.list-enter-active,
.list-leave-active {
  transition: all 1s;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>
