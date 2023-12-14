<script>
import axios from 'axios';
import Cards from './Cards.vue';
import { store } from '../../src/store';
import SeachArea from './SeachArea.vue';
export default {
    components: { Cards, SeachArea },
    data() {
        return {
            store,
            targetArchetype: '' //volevo inserire selectedArchetype ma lo ritenevo più opportuno così da non confondersi con il valore in searcharea
        }                         //è semplicemente una proprietà utilizzata per salvarci dentro il valore dell' archetipo potendolo utilizzare  nel mainArea semplicemente come se fosse una variabile.

    },

    //prendiamo con axios l' array dall' api
    created() {
        axios.get(store.apiURL).then((response) => {
            store.cards = response.data.data;
            console.log(store.cards)
        });
    },
    computed: {
        filteredCards() {
            if (!this.targetArchetype) {
                return this.store.cards; //se non ci sono archetipi riporta tutte le carte
            }
            return this.store.cards.filter(card => card.archetype === this.targetArchetype);
        },
    },
    methods: {
        filterArchetype(archetype) {
            this.targetArchetype = archetype;
        },
    },

}
</script>

<template>
    <SeachArea @search="filterArchetype" />
    <main class="container">

        <!--head con carte trovate-->
        <h4 class="list-head" v-show="filteredCards.length > 0"><!--condizione1-->
            Found {{ filteredCards.length }} cards
        </h4>

        <h4 class="list-head" v-show="filteredCards.length === 0"><!--condizione2-->
            No cards found
        </h4>
        <!--/head con carte trovate-->

        <!--contenitore delle cards-->
        <div class="cardlist flex wrap gap">

            <!--passiamo l' array al compomente figlio assegnando le proprietà per il props-->
            <Cards v-for="card in filteredCards" :name="card.name" :type="card.type"
                :cardImage="card.card_images[0].image_url" />
            <!--entriamo nell' array delle immagini e prendiamo l'url in posizione 0-->

        </div>
        <!--/contenitore delle cards-->
    </main>
</template>

<style scoped lang="scss">
@import "../assets/scss/Utils.scss";

main {
    background-color: $primary;
    padding: 3.125rem;

    .list-head {
        color: $primary;
        background-color: #212529;
        padding: 1.25rem;
    }
}
</style>