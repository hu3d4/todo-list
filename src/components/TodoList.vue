<template>
  <div>
    <div v-for="todo in allTodos" :key="todo.id">
      <TodoItem :todo="todo" />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import TodoItem from '@/components/TodoItem.vue';
import { mapGetters } from 'vuex';

@Component({
  components: {
    TodoItem,
  },
  computed: {
    ...mapGetters(['allTodos']),
  },
})
export default class TodoList extends Vue {}
</script>
