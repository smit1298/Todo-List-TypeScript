<template>
  <div id="id">
    <div class="todolist">
      <h3>Todo List</h3>
      <div class="input-group mb-3">
        <input
          type="text"
          class="form-control"
          placeholder="Todo"
          aria-label="Todo"
          aria-describedby="button-addon2"
          v-model="todoInput"
        />
        <button
          class="btn btn-outline-secondary"
          type="button"
          id="button-addon2"
          @click="addTodo"
        >
          ADD
        </button>
      </div>
    </div>

    <ul class="list-group">
      <li
        v-for="(todo, index) in todoList"
        :key="index"
        :class="{
          'list-group-item': true,
          'list-group-item-secondary': todo.checked,
        }"
        @click="todo.toggleChecked()"
      >
        {{ todo.todo }}
        <button
          type="button"
          class="btn-close"
          data-bs-dismiss="modal"
          aria-label="Close"
          @click.stop="delTodo(todo)"
        ></button>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

class Todo {
  todo: string;
  checked: boolean;

  constructor(todo: string) {
    this.todo = todo;
    this.checked = false;
  }

  toggleChecked() {
    this.checked = !this.checked;
  }
}
@Options({
  props: {
    msg: String,
  },
})
export default class Todolist extends Vue {
  todoInput = "" as string;
  todoList: Todo[] = [];

  addTodo() {
    console.log("todoInput", this.todoInput);
    let todo = new Todo(this.todoInput);
    this.todoList.push(todo);
  }

  delTodo(todo: Todo) {
    console.log("delTodo:", todo);
    this.todoList = this.todoList.filter((todoItem) => {
      return todoItem !== todo;
    });
  }
  mounted() {
    this.todoList.push(new Todo("abcd"));
    this.todoList.push(new Todo("1234"));
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.list-group-item-secondary {
  text-decoration: line-through;
}
</style>
