<template>
  <div>
    <v-text-field
            label="Nome"
            required
            placeholder="valorInicial"
    ></v-text-field>
    <v-btn x-large v-on:click="incrementar">Adicionar</v-btn>
    {{valorInicial}}
  </div>
</template>

<script>
export default {
  data() {
    return {
      qtd: 20,
    }
  },
  props: {
    valorInicial: {
      type: String,
      required: true
    }
  },
  methods: {
    adicionarNome: function(){
      alert("Adicionado");
    },
    incrementar: function(){
      this.$emit('update', this.qtd);
    }
  }
}
</script>
