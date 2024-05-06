<script>
export default {
    props: {
        cardObj: Object,
    },
    computed: {
        image() {
            return this.cardObj.image;
        }
    },
}
</script>

<template>
    <div class="ms_card">
        <img :src="image" alt="">
        <h2 class="text-center mt-3">{{ cardObj.name }}</h2>
        <h3 class="fw-lighter text-center mt-5">{{ cardObj.status }}</h3>
        <h3 class="fw-lighter text-center">{{ cardObj.species }}</h3>
    </div>
</template>

<style scoped lang="scss">
@use "../style/partials/variables" as *;

.ms_card {
    margin-top: 80px;
    color: $main-text-color;

    img {
        border-radius: 50%;
    }

    h3 {
        font-size: 1.5rem;
    }
}
</style>