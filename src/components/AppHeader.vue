<script>
export default {
    data() {
        return {
            name: 'AppHeader',
        }
    }
}
</script>

<template>
    <header>
        <img src="../assets/img/1200px-Yu-Gi-Oh!_(Logo).jpg" alt="">
        <h1>
            Yu-Gi-Oh API
        </h1>
    </header>

</template>

<style scoped lang="scss">
h1 {
    color: black;
    padding: 20px;
}

header {
    height: 150px;
    display: flex;
    align-items: center;

    img {
        max-width: 15%;
    }
}
</style>
