<script>
import axios from 'axios';
import CardItem from './CardItem.vue';
import SelectCardArchetype from './SelectCardArchetype.vue';
export default {
    components: {
        CardItem,
        SelectCardArchetype,
    },
    name: 'AppMain',
    data() {
        return {
            cards: [],
            filteredArchetype: '',
        };

    },
    mounted() {
        this.searchCard();
    },
    methods: {
        searchCard(archetype = '') {
            const urlApi = archetype ? `https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${archetype}` : 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0';
            axios
                .get(urlApi)
                .then((response) => {
                    this.cards = response.data.data;
                })
        },
        ciao(archetype) {
            this.filteredArchetype = archetype;
            console.log(this.filteredArchetype)
            this.searchCard(archetype)
        }
    }
}
</script>

<template>
    <SelectCardArchetype @filtered-archetype="ciao" />
    <section id="jumbotron">
        <div class="container">
            <div class="text-center my-4 text-bg-dark">
                <p>Cards Count: {{ cards.length }}</p>
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