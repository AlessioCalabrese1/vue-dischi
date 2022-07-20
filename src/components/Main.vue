<template>
  <main @search="genreSearchResponse">
    <div class="musics-card-container container">
      <div class="row g-2">
        <MusicCard v-for="(music, index) in filteredMusics" :key="index" v-show="isLoading"
        :musicElement="music"
        />
        
        <GenreSearch :genres="genres" />
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
        filteredMusics: [],
        isLoading: false,
        genres: [],
      }
    },

    methods: {
        getElemementFromApi() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((result) => {
              this.musics = result.data.response;
              this.filteredMusics = this.musics;
              this.sentinell = true;
              this.isLoading = true;
              for (let index = 0; index < this.musics.length; index++) {
                if (this.genres.includes(this.musics[index].genre) == false) {
                    this.genres.push(this.musics[index].genre);
                }
              }
            })
            .catch((error) => {
              console.log("Errore nella ricerca");
              console.log(error);
            })
        },

        genreSearchResponse(genreSelected){
          console.log("arrivato");
          if (genreSelected == "" || genreSelected == null) {
            this.filteredMusics = this.musics;
          } else{
            this.filteredMusics = this.musics.filter( (music) => music.genre.includes(genreSelected));
          }
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