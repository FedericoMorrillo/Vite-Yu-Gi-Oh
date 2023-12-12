<script>
export default {
    data() {
        return {
            tipo: 'alien',
        }
    }

}
</script>

<template>
    <nav class="container">
        <select class="search-bar" v-model="tipo" id="">
            <option value="Alien">Alien</option>
        </select>
    </nav>
</template>

<style scoped lang="scss">
@import "../assets/scss/utils.scss";

.search-bar {
    width: 9.375rem;
    height: 2.5rem;
    margin: 1.5625rem 0;
}
</style>