<template>
  <v-row style="background-color: rgb(1, 52, 16);" >
    <v-col 
      v-for="(filmes, i) in items"
      :key="i"
      cols="12" 
      md="3"
      >
      <v-container>
        <v-hover v-slot="{ isHovering, props }">
          <v-card
            class="mx-auto ml-n5"
            max-width="800"
            v-bind="props"
            height="550"
            theme="dark"
            variant=""
            elevation="18"
            style="background-color: rgb(4, 59, 4);"
          >
            <v-img
              :aspect-ratio="16/9"
              :src="filmes.imagem"
              cover
            >
              <v-expand-transition>
                <div
                  v-if="isHovering"
                  class="d-flex transition-fast-in-fast-out bg-green-darken-2 v-card--reveal text-h2"
                  style="height: 100%;"
                >
                  {{ filmes.filmeAno }}
                </div>
              </v-expand-transition>
            </v-img>

            <v-card-text class="pt-6">
              <div class="font-weight-light text-white text-h6 mb-2 font-weight-bold">
                {{filmes.categoria}}
              </div>

              <h3 class="text-h4 font-weight-light text-green mb-2 font-weight-black">
                {{filmes.nome}}
              </h3>

              <div class="font-weight-light text-h6 mb-2">
                {{filmes.descricao}}
              </div>
            </v-card-text>
          </v-card>
        </v-hover>
      </v-container>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'funcoesPage',
  data () {
    return {
      headers: [
        {
          title: "Nome",
          key: "nome",
        },
        {
          title: "Ano",
          key: "filmeAno",
        },
        {
          title: "Descrição",
          key: "descricao",
        },
        {
          title: "Categoria",
          key: "categoria",
        },
        {
          title: "Imagem",
          key: "imagem",
        },
      ],
      items: [],
    }
  },

  async created(){
      await this.getItens();
    },


    methods: {
      
      async getItens(){
        const response = await this.$api.get('/filmes')
        this.items = response.data

      },
    },
  };

</script>

<style>
  .v-card--reveal {
    align-items: center;
    bottom: 0;
    justify-content: center;
    opacity: .9;
    position: absolute;
    width: 100%;
  }
</style>