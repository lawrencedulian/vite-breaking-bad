<script>
import AppHeader from './components/AppHeader.vue';
import AppSearch from './components/AppSearch.vue';
import CharactersList from './components/CharactersList.vue'

import axios from "axios";
import { store } from "./store";

export default {
  components: {
    AppHeader,
    AppSearch,
    CharactersList
  },
  data() {
    return {
      store
    }
  },
  created() {
    axios.get("https://www.breakingbadapi.com/api/characters").then((resp) => {
      this.store.characters = resp.data;
    })
  }
}
</script>

<template>
  <AppHeader />
  <main class="d-flex flex-column justify-content-center">
    <div class="container">
      <AppSearch />
      <CharactersList />
    </div>

  </main>
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
</style>