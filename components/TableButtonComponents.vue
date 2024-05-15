<template >
        
  <v-data-table
    :headers="headers"
    :items="items"
    style="background-color: rgb(19, 3, 26);" 
  >
        <template v-slot:top>
      <v-toolbar
        flat
        style="background-color: rgb(55, 5, 96);"
      >

        <v-toolbar-title class="justify-center d-flex align-center font-weight-black" >
          <v-icon >
            mdi-table
          </v-icon>
            Tabelinha do Pai
        </v-toolbar-title>
        <v-col cols="auto" >
        <v-btn icon="mdi-plus" size="default" style="background-color: rgb(14, 98, 6)"></v-btn  >
      </v-col>
          <v-divider
              class="mx-4"
              inset
              vertical
          ></v-divider>
      </v-toolbar>
    </template>

    <template 
      v-slot:item.filmeAno="{ item }"
    >
    <span :style="item.filmeAno >= 2000 ? 'color: #e330c2  ;' : 'color: white;'">{{ item.filmeAno }}</span>      
    </template>

    <template v-slot:item.actions="{ items }">
      <v-icon
        class="me-2"
        size="small"
        @click=""
      >
        mdi-pencil
      </v-icon>
      <v-icon
        size="small"
        @click=""
      >
        mdi-delete
      </v-icon>
    </template>
  </v-data-table>
</template>

<style>
.v-table tbody tr:nth-child(even) {
      background-color: rgb(3, 3, 36);
}

.v-table tbody tr:nth-child(odd) {
      background-color: rgb(47, 4, 63);
}

</style>


<script>
  export default {
    name: 'TableButtonComponents',

    props: {
    items:{
      type: Array,
    },
    headers: {
      type: Array,
    },  
  },
  }
</script>