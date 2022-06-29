<template>
  <div class="container">
    <div class="input-group input-group-sm mb-3 mt-2">
      <div class="input-group-prepend">
        <span class="input-group-text" >Tarea
        </span>
      </div>
      <input
        type="text"
        class="form-control"
        placeholder="Agregar Tarea con Enter o click en el botón"
        v-on:keyup.enter="addTodo"
        v-model="todoText"
      />
      <div class="input-group-prepend">
        <button class="btn btn-success" @click="addTodo()">Agregar</button>
      </div>
      <!-- En el componente hijo se pasan con v-bind o ":" los datos que se quieren pasar y para que
      la comunicacion se en 2 direccion se deben pasar con v-on o "@" los methods con el formato
      'v-on:nombre_metodo_en_el_hijo="nombre_metedo_en_el_padre"'  -->
      <TodoItem
        v-bind:todoArrayItems="todos"
        v-on:deletedItem="deleteTodo"
        v-on:toggledItem="toggleTodo"
      />
    </div>
    <button
      v-if="todos.length > 0"
      type="button"
      class="btn btn-danger"
      @click="deleteAllTodos()"
    >
      Eliminar Todas
    </button>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  name: "Todo",
  components: {
    TodoItem,
  },
  data() {
    return {
      todos: [],
      todoText: "",
      initialId: 1,
    };
  },
  methods: {
    addTodo() {
      if (this.todoText && this.todoText.trim()) {
        this.todos.push({
          id: this.initialId,
          text: this.todoText.trim(),
          checked: false,
        });
        this.todoText = "";
        this.initialId++;
      }
    },
    toggleTodo(id) {
      this.todos = this.todos.map((todo) => {
        if (todo.id === id) {
          todo.checked = !todo.checked;
        }
        return todo;
      });
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    deleteAllTodos() {
      this.todos = [];
      this.initialId = 1;
    },
  },
};
</script>

<style>
.text-w {
  width: 300px;
}
</style>