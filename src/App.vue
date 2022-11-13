<script>
import AppHeader from './components/AppHeader.vue';
import AppSearch from './components/AppSearch.vue';
import AppLoading from './components/AppLoading.vue';
import CharactersList from './components/CharactersList.vue'
import AppResult from './components/AppResult.vue';

import axios from "axios";
import { store } from "./store";

export default {
  components: {
    AppHeader,
    AppSearch,
    AppLoading,
    CharactersList,
    AppResult
  },
  data() {
    return {
      store
    }
  },
  created() {
    this.getCharacters();
  },
  methods: {
    getCharacters() {
      this.store.loading = true;

      const paramsUrl = {}
      if (this.store.searchInput) {
        paramsUrl.name = this.store.searchInput;
      }
      if (this.store.categoryInput) {
        paramsUrl.category = this.store.categoryInput;
      }

      axios.get("https://www.breakingbadapi.com/api/characters", {
        params: paramsUrl
      })
        .then((resp) => {
          this.store.characters = resp.data;
        })
        .catch(error => {
          console.log(error);
          this.store.characters = [];
        })
        .finally(() => {
          this.store.loading = false;
        })
    }
  }
}
</script>

<template>
  <AppHeader />
  <main class="d-flex justify-content-center">
    <div class="my-container">
      <section>
        <AppSearch @startSearch="getCharacters" />
      </section>
      <section class="bg-white">
        <AppResult />
        <AppLoading v-if="store.loading" />
        <CharactersList v-else />
      </section>
    </div>

  </main>
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
</style>