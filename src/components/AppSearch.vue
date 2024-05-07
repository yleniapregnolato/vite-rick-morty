<script>
import { store } from "../store";
export default {
    data() {
        return {
            store,
            status: ["All", "alive", "dead", "unknown"]
        };
    },

}
</script>

<template>
    <div class="container">
        <select @change="$emit('filter')" v-model="store.selectedStatus">
            <option :value="condition" v-for="condition in status">{{ condition }}</option>
        </select>
    </div>
</template>
