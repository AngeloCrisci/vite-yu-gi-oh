<script>
import axios from 'axios'
export default {
    name: 'SelectCardArchetype',
    data() {
        return {
            archetypesList: [],
            filteredArchetype: '',
        }
    },
    methods: {
        searchArchetype() {
            axios
                .get('https://db.ygoprodeck.com/api/v7/archetypes.php')
                .then((response) => {
                    this.archetypesList = response.data;
                })
        },
        getArchetype() {
            this.$emit('filtered-archetype', this.filteredArchetype);
        }
    },
    mounted() {
        this.searchArchetype();
    }

}
</script>

<template>
    <select @change="getArchetype" v-model="filteredArchetype" class="form-select" aria-label="Default select example">
        <option value="">Seleziona il tuo archetipo</option>
        <option v-for="archetype in archetypesList" :key="archetype.archetype_name" :value="archetype.archetype_name">
            {{ archetype.archetype_name }} </option>
    </select>

</template>

<style scoped lang="scss"></style>