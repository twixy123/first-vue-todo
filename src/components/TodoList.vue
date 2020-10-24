<template>
  <div>
    <ul>
      <TodoItem
        v-for="(todo, i) of todos"
        v-bind:todo="todo"
        v-bind:ind="i"
        v-on:remove-todo="removeTodo"
      />
    </ul>
  </div>
</template>

<script>
  import TodoItem from "./TodoItem";

  export default {
    name: 'TodoList',
    props: ['todos'],
    components: {
      TodoItem
    },
    methods:{
      removeTodo(id){
        this.$emit('remove-todo', id)
      }
    }
  }
</script>

<style lang="scss" scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
    text-align: center;
  }
</style>