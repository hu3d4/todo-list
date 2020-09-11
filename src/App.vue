<template>
  <div id='app' class='text-body container pt-5'>
    <TodoInput />
    <TodoList />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import TodoInput from '@/components/TodoInput.vue';
import TodoList from '@/components/TodoList.vue';

@Component({
  components: {
    TodoInput,
    TodoList,
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
