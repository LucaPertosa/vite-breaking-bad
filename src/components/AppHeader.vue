<script>
export default {
    name: "AppHeader",
    data() {
        return {

        }
    }
}
</script>

<template>
    <header>
        <div class="container d-flex align-items-center">
            <img src="../assets/pngaaa.com-426278.png" alt="">
            <h1>Yu-Gi-Oh Api</h1>
        </div>
    </header>
</template>

<style scoped lang="scss">
@use "../style/general.scss";
header {
    background-color: white;
}
.container {
    padding: 10px 0;
    img {
        width: 100px;
        height: 60px;
    }
    h1 {
        margin-left: 1rem;
        margin-bottom: 0;
    }
}
</style>