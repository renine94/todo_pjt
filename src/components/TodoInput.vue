<template>
  <div>
    <input type="text" v-model="newTodo" @keypress.enter="writeTodo">
    <button>할일 등록</button>
  </div>
</template>

<script>
export default {
  name: 'TodoInput',
  data() {
    return {
      newTodo: ''
    }
  },
  methods: {
    writeTodo() {
      // TodoView 로 데이터를 보내야함 (부모에게 데이터보내기)
      if (this.newTodo.trim()) {
        this.$emit('create-todo', {
          id: Date.now(),
          content: this.newTodo.trim(),
          isCompleted: false,
        })
      }
      this.newTodo = ''
    }
  }
}
</script>

<style>

</style>
