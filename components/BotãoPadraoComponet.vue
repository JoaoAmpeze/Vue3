<template>
  
  <v-btn
      text="Butão"
      :color="dialog ? 'red' : 'green' "
      @click="emitirevento()"
  ></v-btn>

</template>

<script>
export default {
  name: 'BotaoPadraComponent',
  data(){
    return{

    };
  },

  props: {
    text:{
      type: String,
    },

    dialog:{
      type: Boolean,
    },
  },

  methods:{
    emitirevento(){
      this.$emit('clicouBotao');
    }
  },

};



</script>
