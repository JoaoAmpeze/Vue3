  <template >
    <v-container class="justify-center d-flex font-weight-bold mt-8">
      <hi>Tabela para Edição de Dados</hi>
    </v-container>
      <v-container style="height: 100vh;">
        <img style="height: 100vh" src="https://veja.abril.com.br/wp-content/uploads/2018/07/entrete-ratinho.jpg?quality=90&strip=info&crop=1&resize=1080,565" alt="">
      </v-container>
        <v-container  @deleteItem="deleteItem" style="height: 100vh;" class="justify-center d-flex align-center mt-n16">
            <TableButtonComponents
              :headers="headers"
              :items="items"
            >
            </TableButtonComponents>

            

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
          {
            title: 'Actions',
            key: 'actions',
            sortable: false,
          },
        ],
        items: []
      }
    },



    async created(){
      await this.getItens();
    },


    methods: {
      async de(items){
        this.$emit('deleteitem')

      },
      
      async getItens(){
        const response = await this.$api.get('/filmes')
        this.items = response.data
        console.log(this.items)
      },
    },
  }

  </script>