<script>
import AppHeader from "./components/AppHeader.vue";
import CardsLists from "./components/CardsLists.vue";
import axios from "axios";
import { store } from "./store";

export default {
    components: {
        AppHeader,
        CardsLists
    },
    data() {
        return {
            store
        }
    },
    mounted() {
        axios.get(store.apiURL).then((resp) => {
            this.store.cards = resp.data.data;
        })
    }
}
</script>

<template>
    <AppHeader />
    <div class="ms_background">
        <CardsLists />
    </div>
</template>

<style lang="scss">
@use "./style/general.scss";
@use "./style/partials/variables" as *;

.ms_background {
    background-color: $main-bgc;
    padding: 15px;
}
</style>
