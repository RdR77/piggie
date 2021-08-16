<template>
  <div class="overflow-auto">
    <b-pagination @change="onChange"
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      aria-controls="productosTable"
    ></b-pagination>

    <p class="mt-3">Página actual: {{ currentPage }}</p>

    <b-table class="tabla"
      id="productosTable"
      :items="productosList"
      small
    >
    <template #cell(image)="imagen">
      <b-img class="imagen" :src="imagen.value" alt="Imagen de producto"></b-img>
    </template>
    </b-table>
  </div>
</template>

<script>
  export default {
    props: {
        productosList: Array
    },
    data() {
      return {
        perPage: 5,
        currentPage: 1,
        rows: 20
      }
    },
    methods: {
      onChange(page) {
        this.$emit('paginate', page)
      }
    }
  }

</script>

<style scoped>
table, td {
  vertical-align: middle;
}
img.imagen {
  width: 250px;
  height: 250px;
}
</style>