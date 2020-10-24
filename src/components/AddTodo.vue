<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Create</button>
  </form>
</template>

<script>
  export default {
    data() {
      return {
        title: '',
      }
    },
    methods: {
      onSubmit() {
        if (this.title.trim()) {
          const newTodo = {
            id: Date.now(),
            title: this.title,
            completed: false
          }

          this.$emit('add-todo', newTodo)
          this.title = ''
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  form {
    display: flex;
    justify-content: space-between;
    align-items: center;
    widows: 100%;
  }

  input {
    width: 69%;
    height: 40px;
    padding: .2rem 1rem;
    box-sizing: border-box;
  }

  button {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 29%;
    height: 40px;
    padding: .2rem 0;
    box-sizing: border-box;
  }
</style>