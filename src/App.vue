<script>
import { store } from "./store";
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import AppSearch from "./components/AppSearch.vue";
import AppLoader from "./components/AppLoader.vue"
export default {
    components: { 
        AppHeader, AppMain, AppSearch, AppLoader 
    },

    data() {
        return {
            store,
            isLoading: false,
        };
    },
    created() {
        this.getStatus();
    }, 
    methods: {
        getStatus() {
            this.isLoading = true;
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
                this.store.cardList = resp.data.results;
                this.isLoading = false;
            })
        }
    }  
};
</script>

<template>
    <AppHeader />
    <AppSearch @filter="getStatus" />
    <AppLoader v-if="isLoading"/>
    <AppMain v-else /> 
</template>

<style lang="scss">
@use "./style/partials/variables" as *;

template {
    background-color: $background-color;
}
</style>