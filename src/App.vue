<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
export default {
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
    components: { AppHeader, AppMain }
};
</script>

<template>
    <AppHeader />
    <AppMain :cardsArray="cardsArray" />
</template>

<style lang="scss">
@use "./style/partials/variables" as *;

template {
    background-color: $background-color;
}
</style>