<script>
import axios from 'axios';
export default {
    data() {
        return {
            selectedArchetype: "",

            archetypes: [],
            apiarchURL: "https://db.ygoprodeck.com/api/v7/archetypes.php",
        };

    },
    created() {
        axios.get(this.apiarchURL).then((response) => {
            this.archetypes = response.data;
            console.log(response.data)
        });
    }
}
</script>

<template>
    <!--contenitore-->
    <nav class="container">
        <!--barra di selezione-->
        <select v-model="selectedArchetype" class="search-bar">
            <option value="">All</option>
            <option v-for="archetype in archetypes" :value="archetype.archetype_name">
                {{ archetype.archetype_name }}
            </option>
        </select>
        <!--/barra di selezione-->
    </nav>
    <!--/contenitore-->
</template>

<style scoped lang="scss">
@import "../assets/scss/utils.scss";

.search-bar {
    width: 9.375rem;
    height: 2.5rem;
    margin: 1.5625rem 0 1.5625rem .625rem;

}
</style>