<script>
export default {
    //props
    props: ['name', 'type', 'cardImage'],
}
</script>

<template>
    <!--card-->
    <div class="card">

        <!--immagine-->
        <div class="image">
            <img :src="cardImage" alt="name">
        </div>

        <!--/immagine-->

        <!--nome-->
        <h4 class="name">
            {{ name }}
        </h4>
        <!--/nome-->

        <!--tipo-->
        <div class="type">{{ type }}</div>
        <!--/tipo-->

    </div>
    <!--/card-->
</template>

<style scoped lang="scss">
@import "../assets/scss/Utils.scss";

.card {
    width: calc(100% / 5 - 8px);
    background-color: #d48f38;

    img {
        width: 100%;
    }

    .name {
        color: $primary;
        text-align: center;
        padding: 1.5625rem 0;
    }

    .type {
        text-align: center;
        font-size: .875rem;
        padding-bottom: 1.25rem;
    }
}
</style>