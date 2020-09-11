<template>
  <div>
    <div class="row my-3 justify-content-between">
      <h3 v-if="!editing">{{ todo.title }}</h3>
      <input
        v-else
        @change="todoTextChange"
        @keyup.enter="updateTodoI(todo)"
        :value="todoText"
        type="text"
        class="col form-control"
      />
      <div>
        <button @click="updateTodoI(todo)" class="btn btn-primary mx-2">
          {{ editing ? "Update" : "Edit" }}
        </button>
        <button @click="deleteTodo(todo.id)" class="btn btn-danger">
          Delete
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';
import { mapActions } from 'vuex';

@Component({
  methods: {
    ...mapActions(['deleteTodo', 'updateTodo']),
  },
})
export default class TodoItem extends Vue {
  @Prop({})
  private todo!: string;

  private todoText = '';
  private editing = false;

  private todoTextChange(e: { target: { value: string } }) {
    this.todoText = e.target.value;
  }

  private updateTodoI(todo: { title: string }) {
    this.editing = this.editing === true ? false : true;
    if (this.editing) {
      this.todoText = todo.title;
      this.updateTodo(todo);
    } else {
      todo.title = this.todoText;
    }
  }
}
</script>
