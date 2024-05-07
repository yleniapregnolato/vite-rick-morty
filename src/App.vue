<script>
import { store } from "./store";
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
            store,
        };
    },
    created() {
        this.getStatus();
        // axios
        //     .get("https://rickandmortyapi.com/api/character")
        //     .then((resp) => {
        //         this.cardsArray = resp.data.results;
        //     });
    }, 
    methods: {
        getStatus() {
            const paramObj = {
                status: "",
            }
            if(this.store.selectedStatus !== "All") {
                paramObj.status = this.store.selectedStatus;             
            }

            console.log("get status", this.store.selectedStatus);
            axios
            .get("https://rickandmortyapi.com/api/character", {
                params: paramObj,
            })
            .then((resp) => {
                this.cardsArray = resp.data.results;
            })
        }
    }  
};
</script>

<template>
    <AppHeader />
    <AppSearch @filter="getStatus" />
    <AppMain :cardsArray="cardsArray" />
</template>

<style lang="scss">
@use "./style/partials/variables" as *;

template {
    background-color: $background-color;
}
</style>