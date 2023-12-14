<script>
import axios from 'axios';
export default {
    data() {
        return {
            //proprietà di base della select che prenderà il valore di input selezionato
            selectedArchetype: "",

            archetypes: [],
            apiarchURL: "https://db.ygoprodeck.com/api/v7/archetypes.php",
        };

    },
    created() {
        axios.get(this.apiarchURL).then((response) => {
            this.archetypes = response.data;//ci prendiamo l' array degli archetipi
        });
    },
}
</script>

<template>
    <!--contenitore-->
    <nav class="container">

        <!--barra di selezione-->
        <select v-model="selectedArchetype" class="search-bar"
            @change="$emit('search', selectedArchetype)"><!--il secondo è il parametro-->
            <!--selectedArchetype vuoto che al nuovo input viene aggiornato con il nuovo valore-->
            <option value="">All</option><!--valore vuoto-->
            <option v-for="  archetype   in   archetypes  " :value="archetype.archetype_name">
                <!--valore preso dall' array-->
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