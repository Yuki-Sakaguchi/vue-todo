<template>
  <div id="todo">
    <h2>追加したいタスクを入力してください</h2>
    <div class="input-area">
      <p><input type="text" v-model="newTodo" @keyup.enter="addTack()"></p>
      <div class="controller">
        <div class="btn" @click="addTack()">ADD TASK</div>
        <div class="btn" @click="removeTask()">DELETE FINISHED TASKS</div>
      </div>
    </div>
    <draggable class="taks-list" v-model="todos" @sort="listSort">
      <label class="task-list__item" v-for="(todo, index) in todos" :key="index">
        <input type="checkbox" v-model="todo.editing">
        <input type="checkbox" v-model="todo.done">
        <input v-if="todo.editing" v-model="todo.text" @keyup.enter="todo.editing = !todo.editing">
        <span v-if="!todo.editing">{{ todo.text }}</span>
      </label>
    </draggable>
  </div>
</template>


<script>
import draggable from 'vuedraggable';

const todoName = 'vue-todo-list';

function getTodo() {
  return JSON.parse(localStorage.getItem(todoName));
}

function setTodo(list) {
  localStorage.setItem(todoName, JSON.stringify(list));
}

export default {
  name: 'todo',
  components: {
    draggable,
  },
  data: () => {
    return {
      todos: getTodo() ? getTodo() : [],
      newTodo: '',
    };
  },
  methods: {
    addTack(event) {
      const tmpText = this.newTodo && this.newTodo.trim();
      if (!tmpText) {
        return;
      }
      this.todos.push({
        text: tmpText,
        done: false,
      });
      setTodo(this.todos);
      this.newTodo = '';
    },
    removeTask(event) {
      for (let i = this.todos.length - 1; i >= 0; i--) {
        if (this.todos[i].done) {
          this.todos.splice(i, 1);
        }
      }
      setTodo(this.todos);
    },
    listSort() {
      setTodo(this.todos);
    },
  },
};
</script>



<style lang="scss">
.input-area {

}

.task-list {
  &__item {
    display: block;
    margin: 20px 0;
    padding: 20px;
    border: 1px solid #ccc;
    cursor: pointer;

    &:hover {
      background-color: #eee;
    }
  }
}
</style>
