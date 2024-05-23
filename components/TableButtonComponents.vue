<template>
  <v-data-table
    :headers="headers"
    :items="items"
    style="background-color: rgb(8, 2, 51)"
  >
    <template v-slot:top>
      <v-toolbar flat style="background-color: rgb(16, 11, 162)">
        <v-toolbar-title
          class="justify-center d-flex align-center font-weight-black"
        >
          <v-icon> mdi-table </v-icon>
          Tabelinha do Pai
        </v-toolbar-title>
        <v-col cols="auto">
          <v-btn icon="mdi-plus" size="default" @click="abrirDialog"> </v-btn>
        </v-col>
        <v-divider class="mx-4" inset vertical></v-divider>
      </v-toolbar>
    </template>

    <template v-slot:item.filmeAno="{ item }">
      <span
        :style="item.filmeAno >= 2000 ? 'color: #e330c2  ;' : 'color: white;'"
        >{{ item.filmeAno }}</span
      >
    </template>

    <template v-slot:item.actions="{ item }">
      <v-icon class="me-2" size="small" color="green" @click="editItem(item)">
        mdi-pencil
      </v-icon>
      <v-icon size="small" color="red" @click="deleteItem(item)"> mdi-delete </v-icon>
    </template>
  </v-data-table>
</template>

<style>
.v-table tbody tr:nth-child(even) {
  background-color: rgb(52, 111, 237);
}

.v-table tbody tr:nth-child(odd) {
  background-color: rgb(17, 4, 116);
}
</style>

<script>
export default {
  name: "TableButtonComponents",

  props: {
    items: {
      type: Array,
    },
    headers: {
      type: Array,
    },
  },

  methods: {
    deleteItem(item) {
      this.$emit("deleteItem", item);
    },
    editItem(item) {
      this.$emit("editItem", item);
    },
    abrirDialog() {
      this.$emit("abrirDialog");
    },
  },
};
</script>
