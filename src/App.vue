<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import AppSearch from "./components/AppSearch.vue";
export default {
    components: { 
        AppHeader, AppMain, AppSearch 
    },

    data() {
        return {
            cardsArray: [],
        };
    },
    created() {
        axios
            .get("https://rickandmortyapi.com/api/character")
            .then((resp) => {
                this.cardsArray = resp.data.results;
            });
    },   
};
</script>

<template>
    <AppHeader />
    <AppSearch />
    <AppMain :cardsArray="cardsArray" />
</template>

<style lang="scss">
@use "./style/partials/variables" as *;

template {
    background-color: $background-color;
}
</style>