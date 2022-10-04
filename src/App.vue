<template>
  <div id="app">
    <todolist></todolist>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Todolist from "./components/Todolist.vue";

@Options({
  components: {
    Todolist,
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px;
}
</style>
