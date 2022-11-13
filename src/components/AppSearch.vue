<script>
import { store } from "../store";

export default {
    name: "AppSearch",
    data() {
        return {
            store,
            category: ["Breaking Bad", "Better Call Saul"]
        }
    }
}
</script>

<template>
    <div class="search-box d-flex flex-row mb-5">
        <input type="text" class="form-control" placeholder="Type Here" v-model="store.searchInput">
        <select class="form-select ms-2" v-model="store.categoryInput">
            <option selected>Select...</option>
            <option v-for="(option, index) in category" :value="option" :key="index">
                {{ option }}
            </option>
        </select>
        <button class="btn ms-1" @click="$emit('startSearch')">
            Search
        </button>
    </div>
</template>

<style lang="scss">
@use "../styles/partials/variables" as *;

.search-box {
    width: 100%;

    input {
        width: 40%;
    }

    select {
        width: 20%;
    }

    button {
        background-color: $bg-btn;
        color: white;
    }
}
</style>