  <template style="background-color: black" >
    <v-container style="height: 100vh;" class="justify-center d-flex align-center">
      <TableComponents
        :headers="headers"
        :items="items"
      >
      </TableComponents>
    </v-container>
  </template>



  <script>


  export default {
    data: () => {
      return {
        headers: [
          {
            title: 'nome',
            key: 'nome',
          },
          {
            title: 'Ano',
            key: 'filmeAno',
          },
          {
            title: 'Descrição',
            key: 'descricao',
          },
          {
            title: 'Categoria',
            key: 'categoria',
          },
        ],
        items: []
      }
    },

    async created(){
      await this.getItens();
    },


    methods: {
      deletar(items){

      },
      
      async getItens(){
        const response = await this.$api.get('/filmes')
        this.items = response.data
        console.log(this.items)
      },
    },
  }

  </script>