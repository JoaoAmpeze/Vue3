<template>
  <v-data-table
    :headers="headers"
    :items="items"
    density="compact"
    item-key="name"
  ></v-data-table>

</template>


<script>
  export default {
    name: 'tableComponets',

    props: {
    items:{
      type: Array,
    },
    headers: {
      type: Array
    },
  },
  }

</script>