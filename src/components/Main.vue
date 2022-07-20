<template>
  <main>
    <div class="musics-card-container container">
      <div class="row g-2">
        <MusicCard v-for="(music, index) in musics" :key="index" v-show="isLoading"
        :musicElement="music"
        />
        
        <GenreSearch :allMusics="musics" />
      </div>

      <div class="row g-2">
        <div class="text-center loader" v-show="isLoading != true">
          <img src="https://www.europeanpolice.it/images/loading_08obi1p7.gif" alt="Loading">
        </div>
      </div>
        
    </div>
    
  </main>
</template>

<script>
import axios from 'axios';
import MusicCard from "./MusicCard.vue";
import GenreSearch from './GenreSearch.vue';

export default {
    
    data: function(){
      return{
        musics: [],
        isLoading: false,
      }
    },

    methods: {
        getElemementFromApi() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((result) => {
              this.musics = result.data.response;
              this.sentinell = true;
              this.isLoading = true;
            })
            .catch((error) => {
              console.log("Errore nella ricerca");
              console.log(error);
            })
        }
    },
    created() {
        this.getElemementFromApi();
    },
    components: {
    MusicCard,
    GenreSearch
}
}
</script>

<style lang="scss" scoped>
  main{
    background-color: #1e2d3b;
    height: 95vh;
    padding-top: 70px;
  }

  .musics-card-container{
    width: 60%;
    margin: 0 auto;
  }

  .loader{
    color: white;
    font-size: 25px;
  }
</style>