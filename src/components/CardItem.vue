<script>
export default {
    name: 'CardItem',
    props: {
        card: {
            type: Object,
            required: true
        }

    }

}
</script>

<template>
    <div id="main-content" class="col-6 col-md-4 col-lg-3 mb-3 mt-4 text-center">
        <img :src="card.card_images[0].image_url" :alt="card.name">
        <p class="fw-bolder mt-1 text-white">{{ card.name }}</p>
        <span class="fw-bold">{{ card.type }}</span>
    </div>
</template>

<style scoped lang="scss">
#main-content {

    img {
        height: 400px;
    }

}
</style>