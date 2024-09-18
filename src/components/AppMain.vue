<script>
import axios from 'axios';
import CardItem from './CardItem.vue';
export default {
    components: { CardItem },
    name: 'AppMain',
    props: {
        cardCount: {
            type: Number,
            required: true
        }
    },
    data() {
        return {
            cards: [],
        };

    },
    mounted() {
        this.searchCard();
    },
    methods: {
        searchCard() {
            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                .then((response) => {
                    this.cards = response.data.data;
                })
        }
    }
}
</script>

<template>
    <section id="jumbotron">
        <div class="container">
            <div>
                <span> {{ cardCount }} </span>
            </div>
            <div class="row">
                <CardItem v-for="card in cards" :key="card.id" :card="card" />
            </div>
        </div>
    </section>

</template>

<style scoped lang="scss">
#jumbotron {
    background-color: #D48F3B;
}
</style>