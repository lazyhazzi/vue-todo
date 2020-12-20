<template>
  <div class="clearAllContainer">
    <button type="button" class="clearAllBtn" v-on:click="clearTodo">Clear All</button>
  </div>
</template>

<script>
import { mapMutations } from "vuex";

export default {
  methods: {
    ...mapMutations({
      clearTodo: "clearAllItem"
    })
  }
};
</script>

<style scoped>
.clearAllContainer {
  width: 8.5rem;
  height: 50px;
  background: #fff;
  border-radius: 5px;
  margin: 0 auto;
}
.clearAllBtn {
  color: #e20303;
  display: block;
  width: 100%;
  height: 100%;
}
</style>
