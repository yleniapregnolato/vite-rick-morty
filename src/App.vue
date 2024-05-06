<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
export default {
    data() {
        return {
            cardsArray: [],
        };
    },
    created() {
        axios.get("https://rickandmortyapi.com/api/character")
            .then((resp) => {
            this.cardsArray = resp.data.data;
            // console.log(resp);
        });
    },
    components: { AppHeader }
};
</script>

<template>
  <AppHeader />
</template>

<style lang="scss">
@use "./style/partials/variables" as *;

template {
    background-color: $background-color;
}

</style>