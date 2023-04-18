<script>
import AppHeader from "./components/AppHeader.vue";
import CardsLists from "./components/CardsLists.vue";
import AppLoader from "./components/AppLoader.vue";
import AppFinder from "./components/AppFinder.vue";
import axios from "axios";
import { store } from "./store";

export default {
    components: {
        AppHeader,
        AppFinder,
        CardsLists,
        AppLoader
    },
    data() {
        return {
            store,
            archetype: ["Archfiend", "Ally of Justice", "Ancient Gear"],
        }
    },
    mounted() {
        store.loading = true
        axios.get(store.apiURL, {
            params: {
                num: 100,
                offset: 0,
            }
        }).then((resp) => {
            this.store.cards = resp.data.data;
            this.cardNumber = store.cards.length;
            store.loading = false;
        })
    }
}
</script>

<template>
    <AppHeader />
    <AppFinder :archetype="archetype"/>
    <AppLoader v-if="store.loading"/>
    <CardsLists v-else/>
</template>

<style lang="scss">
@use "./style/general.scss";
@use "./style/partials/variables" as *;

.ms_background {
    background-color: $main-bgc;
    padding: 15px;
}
</style>