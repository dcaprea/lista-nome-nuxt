<template>
    <div>
      <NuxtLink to="/">Home page</NuxtLink>
      <div
        :class="[`text-${title[0]}`, `mb-${title[2]}`]"
        class="transition-swing"
        v-text="title[1]"
      >
      </div>
    <Input v-on:salvar="adicionarNome" />
    </div>
</template>


<script>
  import Input from './../components/Input'

export default {
  name: 'Adicionar',
  components: {
    'Input': Input
  },
  data(){
    return {
      title: ['h1', 'Adicionar Nome', 6],
      items: [],
      nome: "Daniel Aprea",
      novoNome: "",
    }
  },
  methods: {
    async adicionarNome(valor) {
      /*this.novoNome = valor;*/

      this.$axios.$post('http://localhost:3004/nomes', {
        nome: valor
      });
      /*const nome = await this.$axios.$get('http://localhost:3004/nomes')
      this.items = nome
      this.load = false;*/
    }
  }
}
</script>
