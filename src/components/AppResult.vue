<script>
import { store } from "../store";
export default {
    data() {
        return {
            store,
        }
    }
}
</script>
    
<template>
    <div>
        Totale risultati: {{ store.cardList.length }}
    </div>
</template>