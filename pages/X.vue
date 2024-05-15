<template>
  <body style="background-color: rgb(0,0,0);">
    <v-row align="center" justify="center">
      <v-col class="text-center">
        <div>
          <img  src="https://upload.wikimedia.org/wikipedia/commons/9/95/Twitter_new_X_logo.png">
        </div>
      </v-col>
      <v-col class="text-start">
          <v-container class="mt-15">
            <h1 class="font-weight-bold text-h2 "> Acontecendo agora</h1>  
          </v-container>
          <v-container class="mt-8">
            <h2 class="font-weight-black font-weight-medium " >Inscreva-se hoje</h2>
          </v-container>
          <v-container >
              <v-btn 
                @click="dialog = true" 
                style="background-color: #ffffff; color: #000000; " 
                rounded="xl" 
                size="x-large" b
                lock
                
              >
              <v-icon>
                mdi-google
              </v-icon>
                    Inscrever-se no Google
              </v-btn>
            </v-container>
          <v-container class="mt-n7">
              <v-btn 
                @click="dialog = true" 
                style="background-color: #ffffff; color: #000000; " 
                rounded="xl" 
                size="x-large" b
                lock
              >
              <v-icon>
                mdi-apple
              </v-icon>
                  Inscrever-se com Apple
              </v-btn>
              <v-container>
              <p>--------------------------ou---------------------</p>
              </v-container>
            </v-container>
            <v-container class="mt-n8 justify-self-center d-flex align-self-center ">
              <v-btn 
                @click="dialog = true" 
                style="background-color: #1d9bf0; color: #f1f9ff; " 
                rounded="xl" 
                size="x-large" b
                lock
              >
              
                  Criar Conta         
                  
              </v-btn>
            </v-container>
        <div class="text-start pa-4">
          <v-dialog
            v-model="dialog"
            width="500"    
          >

            <v-card
              max-width="100%"
              title="Criar conta"
              style="background-color: black; color: #f9f9f9;"
            >
              <template v-slot:actions>
                <v-btn
                  class="ms-auto"
                  @click="dialog = false" 
                >
                  <v-icon>
                    mdi-alpha-x
                  </v-icon>
                </v-btn>
                <v-sheet class="bg-deep-purple pa-12" rounded>
                  <v-card class="mx-auto px-6 py-8" max-width="344">
                    <v-form
                      v-model="form"
                      @submit.prevent="onSubmit"
                    >
                      <v-text-field
                        v-model="email"
                        :readonly="loading"
                        :rules="[required]"
                        class="mb-2"
                        label="Email"
                        clearable
                      ></v-text-field>

                      <v-text-field
                        v-model="password"
                        :readonly="loading"
                        :rules="[required]"
                        label="Password"
                        placeholder="Enter your password"
                        clearable
                      ></v-text-field>

                      <br>

                      <v-btn
                        :disabled="!form"
                        :loading="loading"
                        color="success"
                        size="large"
                        type="submit"
                        variant="elevated"
                        block
                      >
                        Sign In
                      </v-btn>
                    </v-form>
                  </v-card>
                </v-sheet>
              </template>
            </v-card>
          </v-dialog>
        </div>
      </v-col>
    </v-row>
  </body>
</template>

<script>
export default {
  data: () => {
    return {
      dialog: false,
      valor: 0,
      form: false,
      email: null,
      password: null,
      loading: false, 
    }
  },

  created(){

  },

  watch: {
    dialog(evento) {
      this.valor++
    }
  },

  methods: {
      onSubmit () {
        if (!this.form) return

        this.loading = true

        setTimeout(() => (this.loading = false), 2000)
      },
      required (v) {
        return !!v || 'Field is required'
      },
    },
  }
</script>