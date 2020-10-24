<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed">
      <strong>{{ind + 1}}</strong>
      {{todo.title | upperCase}}
    </span>
    <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
  export default {
    props:{
      todo:{
        type: Object,
        required: true
      },
      ind:Number
    },
    filters: {
      upperCase(value){
        return value.toUpperCase()
      }
    }
  }
</script>

<style lang="scss" scoped>
  input{
    margin-right: 1rem;
  }
  li{
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    margin-bottom: 1rem;
    padding: .5rem 2rem;
  }

  .rm{
    background: red;
    color: #fff;
    border-radius: 50%;
    font-weight: bold;
    border: none;
    outline: none;
    cursor: pointer;
  }

  .done{
    text-decoration: line-through;
  }
</style>