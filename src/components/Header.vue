<template>
  <header>
    <img :src="require('../assets/logo.svg')" alt="LogoSpotify">
  </header>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
    header{
        height: 5vh;
        background-color: #2e3a46;
    }

    img{
        height: calc(100% - 20px);
        margin: 10px;
    }
</style>