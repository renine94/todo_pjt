<template>
  <div>
    <TodoInput @create-todo="createTodo" />
    <TodoList :todos="todos" @checked="updateTodo"/>
  </div>
</template>

<script>
import TodoInput from '@/components/TodoInput.vue' // @ -> src/
import TodoList from '../components/TodoList.vue'

export default {
  name: 'TodoView',
  components: {
    TodoInput,
    TodoList,
  },
  data() {
    return {
      todos: [
        { id: 1, content: 'Django 복습', isCompleted: true },
        { id: 2, content: 'JavaScript 복습', isCompleted: false },
        { id: 3, content: 'Vue CLI 학습', isCompleted: false },
      ]
    }
  },
  methods: {
    // emit 에서 todo 데이터를 보내줘서 인자로 todo를 받는다.
    updateTodo(todo) {
      todo.isCompleted = !todo.isCompleted
    },
    createTodo(todo) {
      this.todos.push(todo)
    }
  },
}
</script>

<style>

</style>
