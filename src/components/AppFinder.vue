<script>
import axios from "axios";
import { store } from "../store";

export default {
    name: "AppFinder",
    props: {
        archetype: Array,
    },
    data() {
        return {
            store,
            selectedArchetype: "",
            cardNumber: 0,
        }
    },mounted() {
        this.getCardRequest()
    },
    methods: {
        handleChange() {
            if (this.selectedArchetype) {
                axios
                .get(store.apiURL, {
                    params: {
                        archetype: this.selectedArchetype,
                        num: 100,
                        offset: 0,
                    }
                })
                .then((resp) => {
                    this.store.cards = resp.data.data;
                    this.cardNumber = store.cards.length;
                })
            } else {
                this.getCardRequest();
            }
        },
        getCardRequest() {
            axios
            .get(store.apiURL, {
                params: {
                    num: 100,
                    offset: 0,
                }
            })
            .then((resp) => {
                this.store.cards = resp.data.data;
                this.cardNumber = store.cards.length;
            });
        },
    }
}
</script>

<template>
    <div class="ms_background">
        <div class="container mb-3 p-0">
            <label for="arch">Archetype</label>
            <select @change="handleChange" v-model="selectedArchetype" class="rounded-1" name="card-type" id="arch">
                <option value="">All</option>
                <option v-for="elem in archetype" :value="elem">{{ elem }}</option>
            </select>
        </div>
    </div>
    <div class="ms_background_2">
        <div class="container mb-3 p-1">
            <span class="findertext">
                Sono state trovate {{ cardNumber }} carte
            </span>
        </div>
    </div>
</template>

<style lang="scss">
@use "../style/general.scss";
@use "../style/partials/variables" as *;

.ms_background {
    background-color: $main-bgc;
    padding: 15px;
}
.ms_background_2 {
    background-image: linear-gradient(90deg,$second-color, $main-bgc, $second-color);
    padding: 15px;
    color: white;
}
.findertext {
    font-size: 1.5rem;
}
</style>