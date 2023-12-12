<script>
import axios from 'axios';
import Cards from './Cards.vue';
import { store } from '../../src/store';
export default {
    components: { Cards },
    data() {
        return {
            store,
        }
    },

    //prendiamo con axios l' array dall' api
    created() {
        axios.get(store.apiURL).then((response) => {
            store.cards = response.data.data;
            console.log(store.cards)
        });
    }
}
</script>

<template>
    <main class="container">
        <!--head con carte trovate-->
        <h4 class="list-head">
            Found {{ store.cards.length }} cards
        </h4>
        <!--/head con carte trovate-->

        <!--contenitore delle cards-->
        <div class="cardlist flex wrap">
            <!--passiamo l' array al compomente figlios-->
            <Cards :cards="store.cards" />
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