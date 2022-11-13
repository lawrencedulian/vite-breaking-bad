<script>
import { store } from "../store";
export default {
    name: "AppResult",
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="message text-center p-1">
        <h5 v-if="this.store.characters.length === 0">Sorry, the search returned no results.
        </h5>
        <h5 v-else>
            We Found {{ this.store.characters.length }}
            {{ this.store.characters.length === 1 ? 'character' : 'characters' }}
        </h5>
    </div>
</template>

<style lang="scss">
@use "../styles/partials/variables" as *;

.message {
    width: 100%;
    height: 50px;
    color: white;
    background-color: $bg-message;
}
</style>