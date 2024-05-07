<script>
import { store } from "../store";
import AppResult from "./AppResult.vue";
export default {
    data() {
        return {
            store,
            status: ["All", "alive", "dead", "unknown"]
        };
    },
    components: { AppResult }
}
</script>

<template>
    <div class="container d-flex justify-content-between px-4">
        <select @change="$emit('filter')" v-model="store.selectedStatus">
            <option :value="condition" v-for="condition in status">{{ condition }}</option>
        </select>
        <AppResult />
    </div>
    
</template>
