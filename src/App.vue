<script>
import AppHeader from "./components/AppHeader.vue";
import CardsLists from "./components/CardsLists.vue";
import AppLoader from "./components/AppLoader.vue";
import axios from "axios";
import { store } from "./store";

export default {
    components: {
        AppHeader,
        CardsLists,
        AppLoader
    },
    data() {
        return {
            store
        }
    },
    mounted() {
        store.loading = true
        axios.get(store.apiURL, {
            params: {
                num: 40,
                offset: 0,
            }
        }).then((resp) => {
            this.store.cards = resp.data.data;
            store.loading = false
        })
    }
}
</script>

<template>
    <AppHeader />
    <AppLoader v-if="store.loading"/>
    
    <div class="ms_background" v-else>
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
