<script>
export default {
    name: "CharacterCard",
    props: {
        character: Object
    }
}
</script>

<template>
    <div class="card d-flex text-center ">
        <img class="mx-auto d-block" :src="character.img" alt="">


        <div class="description text-center mt-2">
            <h5>{{ character.name.toUpperCase() }}</h5>
            <p> {{ character.category }}</p>
            <p> {{ character.status }}</p>
        </div>

    </div>
</template>

<style lang="scss" scoped>
@use "../styles/partials/variables" as *;

.card {
    min-height: 300px;
    border-radius: 0;
    background-color: $main-bg-color;

    img {
        width: 70%;
    }

    h5 {
        font-size: 13px;
        color: white;
    }

    .description {
        color: gray;
    }
}
</style>
