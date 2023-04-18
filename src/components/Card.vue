<script>
export default {
    name: "Card",
    props: {
        name: String,
        archetype: String,
        img: String,
    },
}
</script>

<template>
    <div class="card mb-4 text-center ms_background1">
        <img class="card-img-top" :src="img" :alt="name">
        <div class="ms_card-body">
            <h3 class="ms_card-title">{{ name }}</h3>
            <p class="card-text">{{ archetype }}</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>
@use "../style/partials/variables" as *;
.ms_background1 {
    background-color: white;
}
.ms_card-title {
    font-size: 1rem;
    font-weight: 700;
    color: $title-color;
}
.ms_card-body {
    height: 120px;
    padding: 15px 0;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
}
</style>