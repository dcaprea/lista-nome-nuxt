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

    <ul v-if="!load" class="lista-nomes">
      <li v-for="item in items" :key="item.id">
        {{ item.nome }}
        <v-icon
          :id="item.id"
          v-on:click="deleteItem(`${item.id}`)"
          medium
          color="red darken-2"
        >
          mdi-delete
        </v-icon>
      </li>
    </ul>
      <v-btn
        class="ma-1"
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
    this.load = true
    this.listUsers()
  },
  data(){
    return {
      load: false,
      title: ['h1', 'Lista Nome', 6],
      items: [],
    }
  },
  methods: {
    async listUsers() {
      const nome = await this.$axios.$get('http://localhost:3004/nomes')
      this.items = nome
      this.load = false
    },
    deleteItem(id){
      this.load = true
      this.$axios.$delete(`http://localhost:3004/nomes/${id}`
      ).then(
        () => {
          this.listUsers()
        }
      )
    }
  }
}
</script>

<style lang="scss">
  .lista-nomes{
    list-style: none;
  }
  li{
    margin-bottom:10px;
  }
</style>
