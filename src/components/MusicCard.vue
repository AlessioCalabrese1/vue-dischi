<template>
  <div class="music-card-element p-3">
    <div>
        <img class="img-fluid" :src="musicElement.poster" alt="Poster">
    </div>

    <div class="text-center music-element-info">
        <p class="mt-3">
            {{ musicElement.title }}
        </p>

        <div>
            {{ musicElement.author }} <br>
            {{ musicElement.year }}
        </div>
    </div>
  </div>
</template>

<script>
export default {
    props:{
        musicElement:{
            type: Object,
            required: true,
        }
    }
}
</script>

<style lang="scss" scoped>
    .music-card-element{
        width: calc((100% / 5) - 2.5rem);
        background-color: #2e3a46;
        margin: 10px 20px;
    }
    .music-element-info{
        color: white;

        p{
            font-weight: bold;
            font-size: 18px;
            text-transform: uppercase;
        }

        div{
            color: #606d74;
            font-weight: bold;
        }
    }
</style>