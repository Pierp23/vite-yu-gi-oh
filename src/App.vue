<script>
import HeaderComponent from './components/HeaderComponent.vue'
import MainComponent from './components/MainComponent.vue'
import Axios from 'axios'

export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent

  },
  data() {
    return {
      characters: {}
    }
  },
  methods: {

  },
  created() {
    Axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
      .then(response => {
        this.characters = response.data.data
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
