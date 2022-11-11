<script>
export default {
    name: "CharacterCard",
    props: {
        character: Object
    }
}
</script>

<template>
    <div class="card p-2">
        <img :src="character.img" alt="">
        <h5>{{ character.name.toUpperCase() }}</h5>

        <div class="description">
            <p>Breaking Bad</p>
            <p> {{ character.status }}</p>
        </div>

    </div>
</template>

<style lang="scss" scoped>
@use "../styles/partials/variables" as *;

.card {
    background-color: $main-bg-color;
}
</style>
