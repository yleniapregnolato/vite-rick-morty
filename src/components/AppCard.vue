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
        <h2>{{ cardObj.name }}</h2>
        <h3>{{ cardObj.status }}</h3>
        <h3>{{ cardObj.species }}</h3>
    </div>

</template>

<style scoped lang="scss">
</style>