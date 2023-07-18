<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import Axios from 'axios';
import { store } from './store.js';

export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent

  },
  data() {
    return {
      store
    }
  },
  methods: {
    getCard() {
      Axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
        .then(response => {
          this.store.characters = response.data.data
        })
    }
    ,
    getArchetype() {
      Axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
        .then(response => {
          this.store.archetypes = response.data
          // console.log(this.store.archetypes)
        })
    },
    filterArchetype() {
      this.getCard,
        Axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0', {
          params: {
            archetype: this.store.searchArchetype
          }
        })
          .then(response => {
            this.store.characters = response.data.data
          })
          .catch(error => {
            this.store.characters = []
          })


    }

  },
  created() {
    this.getCard(),

      this.getArchetype()
  }
}
</script>

<template>
  <HeaderComponent />

  <MainComponent @search="filterArchetype()" />
</template>

<style lang="scss">
@use "./assets/scss/main.scss";
@use "./assets/scss/reset.scss";
</style>
