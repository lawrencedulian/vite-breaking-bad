<script>
import AppHeader from './components/AppHeader.vue';
import AppSearch from './components/AppSearch.vue';
import AppLoading from './components/AppLoading.vue';
import CharactersList from './components/CharactersList.vue'

import axios from "axios";
import { store } from "./store";

export default {
  components: {
    AppHeader,
    AppSearch,
    AppLoading,
    CharactersList
  },
  data() {
    return {
      store
    }
  },
  created() {
    this.store.loading = true;
    axios.get("https://www.breakingbadapi.com/api/characters?limit=5").then((resp) => {
      this.store.characters = resp.data;
    })
      .finally(() => {
        this.store.loading = false;
      })
  },
  methods: {

  }
}
</script>

<template>
  <AppHeader />
  <main class="d-flex justify-content-center">
    <div class="my-container">
      <section>
        <AppSearch />
      </section>
      <section class="bg-white">
        <AppLoading v-if="store.loading" />
        <CharactersList v-else />
      </section>
    </div>

  </main>
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
</style>