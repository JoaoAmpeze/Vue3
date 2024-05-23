<template>
  <v-container
    style="height: 100vh"
    class="justify-center d-flex align-center mt-n16"
  >
    <TableButtonComponents
      @abrirDialog="openDialog()"
      @editItem="editItem"
      @deleteItem="deleteItems"
      :headers="headers"
      :items="items"
    >
    </TableButtonComponents>
  </v-container>
  <v-dialog v-model="ativo" width="auto">
    <v-card >
      <h2 class="justify-center d-flex align-center">
      {{ tituloDialog }} Dados
      </h2>
      <v-form>
        <v-container style="width: 80vh">
          <v-row>
            <v-col cols="12" sm="25">
              <v-text-field label="Nome" v-model="filmes.nome"></v-text-field>
            </v-col>

            <v-col cols="12" sm="25">
              <v-text-field
                label="Descrição"
                v-model="filmes.descricao"
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="12">
              <v-autocomplete
                v-model="filmes.categoria"
                :items="categoras"
                label="Categoria"
              ></v-autocomplete>
            </v-col>

            <v-col cols="12" sm="6">
              <v-text-field label="Ano" v-model="filmes.filmeAno"></v-text-field>
            </v-col>

            <v-col cols="12" sm="6">
              <v-text-field label="imagem" v-model="filmes.imagem"></v-text-field>
            </v-col>

          </v-row>
        </v-container>
      </v-form>
      <template v-slot:actions>
        <v-btn
          style="background-color: green"
          color="white"
          class="ms-auto"
          text="Add"
          @click="persist"
        ></v-btn>
      </template>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data: () => {
    return {
      dialog: false,
      ativo: false,
      valor: 0,
      filmes: {
        id: null,
        nome: null,
        filmeAno: null,
        descricao: null,
        categoria: null,
        imagem:null,
      },

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
          title: "Actions",
          key: "actions",
          sortable: false,
        },
      ],
      items: [],
      categoras: [
        'Ação',
        'Drama',
        'Fantasia',
        'Crime',
        'Animação',
        'Ficção Científica',
        'Aventura',
        'Biografia',
        'Guerra',
        'Romance'
      ],
    };
  },


  async created() {
    await this.getItems();
  },

  computed: {
    tituloDialog: function () {
      return this.filmes.id ? "Editar" : "Criar";
    },
  },

  watch: {
    ativo(valor) {
      if (valor == false) {
        this.resetfilmes();
      }
    },
  },

  methods: {
    resetfilmes() {
      this.filmes = {
        id: null,
        nome: null,
        ano: null,
        descricao: null,
        categoria: null,
        imagem:null,
      };
      this.ativo = false;
    },

    async persist() {
      if (this.filmes.id) {
        const response = await this.$api.post(
          `/filmes/persist/${this.filmes.id}`,
          this.filmes
        );
      } else {
        const response = await this.$api.post("/filmes/persist", this.filmes);
      }
      this.resetfilmes();
      await this.getItems();
    },

    editItem(items) {
      console.log(items);
      this.filmes = {
        ...items,
      };
      this.ativo = true;
    },
    async deleteItems(items) {
      if (confirm(`Deseja deletar o registro com id ${items.id}`)) {
        const response = await this.$api.post("/filmes/destroy", {id: items.id});
        console.log(response)
        if (response.type == "error") {
          alert(response.message);
        }
      }
      await this.getItems();
    },
    async getItems() {
      const response = await this.$api.get("/filmes");
      this.items = response.data;
      this.loading = false;
    },
    openDialog() {
      this.ativo = true
    }
  },
};
</script>
