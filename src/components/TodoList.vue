<template>
  <div>
    <h1>TodoList</h1>
    <ul class="todo-list">
      <!-- Todo 목록을 보여줄 예정 -->
      <li v-for="todo in todos" :key="todo.id" :class="{ completed: todo.isCompleted }">
        <input type="checkbox" :checked="todo.isCompleted" @click="$emit('checked', todo)">
        {{ todo.content }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  // Django의 models.py 정의하는거랑 비슷한 느낌.
  // 정의하는 방법은 되게 여러가지이다.
  props: {
    todos: {
      type: Array,
      required: true
    }
  }
}
</script>

<style>
  .completed {
    text-decoration: line-through;
  }

  .todo-list {
    list-style-type: none;
  }
</style>
