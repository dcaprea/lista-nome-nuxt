<template>
    <div>
      <NuxtLink to="/">Home page</NuxtLink>
      <div
        :class="[`text-${title[0]}`, `mb-${title[2]}`]"
        class="transition-swing"
        v-text="title[1]"
      >
      </div>
    <Input v-on:salvar="addUser" />
    </div>
</template>


<script>
import Input from '../components/Input/Input'
import Toasted from 'vue-toasted';

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
      novoId: ""
    }
  },
  methods: {
    numberUsers() {
      try{
      this.$axios.$get('http://localhost:3004/nomes').then(
        (nome) => {
          this.novoId = nome.lenght;
        }
      )
      }catch(error){
        console.log(error)
      }
    },
    addUser(valor) {
      this.numberUsers();
      this.$axios.$post('http://localhost:3004/nomes', {
        nome: valor,
        id: this.novoId
      }).then(
        this.$toasted.show('hello billo')
      )
    }
  }
}
</script>
