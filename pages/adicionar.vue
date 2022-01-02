<template>
    <div>
      <div
        :class="[`text-${title[0]}`, `mb-${title[2]}`]"
        class="transition-swing"
        v-text="title[1]"
      >
      </div>
    <Input :valorInicial="nome"  v-on:update="updateCart" />
    {{quantidade}}
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
      quantidade: 0,
    }
  },
  methods: {
    updateCart(valor) {
      this.quantidade = valor;
      //this.quantidade = valor;
    }
  }
}
</script>
