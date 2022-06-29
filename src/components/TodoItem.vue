<template>
  <div class="container">
    <table class="table table-dark table-striped mt-4" v-if="todoArrayItems.length > 0">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Tarea</th>
          <th scope="col">Estado</th>
          <th scope="col">Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="todo in todoArrayItems" :key="todo.id">
          <th scope="row">{{ todo.id }}</th>
          <td>{{ todo.text }}</td>
          <td
            :class="{
              'text-warning': todo.checked,
              'text-success': !todo.checked,
            }"
          >
            {{ todo.checked ? "Completada" : "Pendiente" }}
          </td>
          <td>
            <a
              class="btn btn-sm p-0 m-1"
              :class="{
                'btn-warning': todo.checked,
                'btn-success': !todo.checked,
              }"
            >
              <img
                src="../assets/pencil.svg"
                width="20"
                height="20"
                alt="Cambiar"
                title="Completar // Pendiente"
                @click="toggleItem(todo.id)"
              />
            </a>
            <a class="btn btn-danger btn-sm p-0 m-1">
              <img
                src="../assets/trash.svg"
                width="20"
                height="20"
                alt="Borrar"
                title="Borrar Seleccionados"
                @click="deleteItem(todo.id)"
              />
            </a>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todoArrayItems: Array,
  },
  methods: {
    // La declaracion de los metodos son :
    // los nombres como se llaman dentro del hijo, en el cuerpo la llamada es:
    // this.$emit("nombre_del_metodo_como_se_llama_en_la_declaracion_del_Componenete_hijo_en_el Padre",parametros si los tiene)
    deleteItem(id) {
      this.$emit("deletedItem", id);
    },
    toggleItem(id) {
      this.$emit("toggledItem", id);
    },
  },
};
</script>

<style>
</style>