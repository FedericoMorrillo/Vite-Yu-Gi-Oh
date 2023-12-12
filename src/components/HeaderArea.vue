<script>
export default {
}
</script>

<template>
    <header class="flex align-c">
        <div class="logo">
            <!--temporanea****-->
            <img src="../assets/logo.jpg" alt="logo">
            <!--/temporanea****-->
        </div>
        <div class="title">
            Yu-Gi-Oh Api
        </div>
    </header>
</template>

<style scoped lang="scss">
@import "../assets/scss/utils.scss";

header {
    background-color: $primary;
}

.logo {
    width: 60px;
    margin: 0 1.5625rem;

    img {
        width: 100%;
    }
}

.title {
    font-size: 1.875rem;
    padding: 1.25rem 0;
}
</style>