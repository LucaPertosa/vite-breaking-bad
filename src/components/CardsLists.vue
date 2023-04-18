<script>
import Card from "./Card.vue";
import { store } from '../store';
export default {
    name: "CardsLists",
    components: {
        Card,
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <main class="ms_background">
        <div class="container ms_background-w py-3">
            <h2 class="text-center mb-3">Lista dei personaggi</h2>
            <div class="row row-cols-5">
                <div class="col" v-for="card in store.cards" :key="card.id">
                    <Card :name="card.name" :archetype="card.archetype" :img="card.card_images[0].image_url"/>
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped lang="scss">
@use "../style/partials/variables" as *;

</style>