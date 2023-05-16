<script setup>
import TodoItem from './TodoItem.vue';
import {Icon} from "@iconify/vue"

// pass todos and isOpen as a props
defineProps({
  todos: Array,
  isOpen: Boolean,
});
</script>

<template>
    <div class="drawer" :class="{open: isOpen}">
      <ul class="todo-list" v-if="todos.length > 0">
        <TodoItem 
        v-for="(todo, index) in todos" 
        :todo="todo" 
        :index="index" 
        readonly
        />
      </ul>
      <p class="todos-msg" v-else>
        <Icon icon="noto-v1:sad-but-relieved-face" width="22"/>
        <span> No completed todos yet! Keep working!</span>
      </p>
    </div>
</template>

  
<style scoped lang="scss">
.drawer {
  position: fixed;
  top: 0;
  right: 0;
  width: 0;
  height: 100vh;
  background-color: #f1f1f1;
  overflow-x: hidden;
  transition: 0.5s;

  &.open {
    width: 33.33%;
  }
}
</style>
