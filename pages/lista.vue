<template>
  <div>
    <div
      :class="[`text-${title[0]}`, `mb-${title[2]}`]"
      class="transition-swing"
      v-text="title[1]"
    >
    </div>

    <div class="text-center" v-if="load">
    <v-progress-circular
      indeterminate
      color="primary"
    ></v-progress-circular>
    </div>

    <ul v-if="!load">
      <li v-for="item in items" :key="item.id">
        {{ item.nome }}
      </li>
    </ul>
      <v-btn
        class="ma-2"
        color="primary"
        dark
        to="/adicionar"
      >
        Adicionar
        <v-icon
          dark
          right
        >
          mdi-checkbox-marked-circle
        </v-icon>
      </v-btn>
  </div>
</template>


<script>

export default {
  name: 'Listar',
  mounted: function(){
    this.load = true;
    this.listaUsuarios();
  },
  data(){
    return {
      load: false,
      title: ['h1', 'Lista Nome', 6],
      items: [],
    }
  },
  methods: {
    async listaUsuarios() {
      const nome = await this.$axios.$get('http://localhost:3004/nomes')
      this.items = nome
      this.load = false;
    }
  }
}
</script>
