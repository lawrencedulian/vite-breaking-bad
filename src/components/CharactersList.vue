<script>
import { store } from "../store";
import CharacterCard from "./CharacterCard.vue";

export default {
    name: "CharactersList",
    components: {
        CharacterCard
    },
    data() {
        return {
            store,
        }
    }
}
</script>

<template>
    <div class="row row-cols-5 g-4">
        <div class="col" v-for="character in store.characters" :key="character.id">
            <CharacterCard :character="character" />
        </div>

    </div>
</template>

<style lang="scss">
@use "../styles/partials/variables" as *;
</style>