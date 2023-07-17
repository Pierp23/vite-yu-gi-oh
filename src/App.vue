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

  },
  created() {
    Axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
      .then(response => {
        this.store.characters = response.data.data
      })
  }
}
</script>

<template>
  <HeaderComponent />

  <MainComponent :characters="characters" />
</template>

<style lang="scss">
@use "./assets/scss/main.scss";
@use "./assets/scss/reset.scss";
</style>
