<template>
  <div>
    <div class="row">
      <input
        @change="todoTextChange"
        @keyup.enter="addTodoI"
        :value="todoText"
        class="col form-control mr-2"
        type="text"
      />
      <button @click="addTodoI" class="btn btn-primary">Add</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { mapActions } from 'vuex';
import { v1 } from 'uuid';

@Component({
  methods: {
    ...mapActions(['addTodo']),
  },
})
export default class TodoInput extends Vue {
  private todoText = '';
  private todoTextChange(e: { target: { value: string } }) {
    this.todoText = e.target.value;
  }
  private addTodoI() {
    if (!this.todoText) {
      return;
    }
    this.addTodo({
      id: v1(),
      title: this.todoText,
    });
    this.todoText = '';
  }
}
</script>
