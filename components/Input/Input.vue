<template>
  <div>
    <v-text-field
            label="Nome"
            required
            v-model="valor"
    ></v-text-field>
    <v-btn x-large v-on:click="adicionarNome">Adicionar</v-btn>
  </div>
</template>

<script>
export default {
  data() {
    return {
      valor: "",
    }
  },
  methods: {
    adicionarNome: function(){
      this.$emit('salvar', this.valor);
      this.valor = "";
    }
  }
}
</script>
