<template>
  <main>
    <div class="musics-card-container container">
      <div class="row g-2 justify-content-center">

        <SearchItems :genres="genres" :artists="artists" class="search" @principal="searchResponse" />
        <MusicCard v-for="(music, index) in filteredMusics" :key="index" v-show="isLoading"
        :musicElement="music"
        />
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
import ArtistSearch from './ArtistSearch.vue';
import SearchItems from './SearchItems.vue';

export default {
    
    data: function(){
      return{
        musics: [],
        filteredMusics: [],
        isLoading: false,
        genres: [],
        artists: [],
        searchSentinell: [false, false],
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
                if (this.artists.includes(this.musics[index].author) == false) {
                    this.artists.push(this.musics[index].author);
                }
              }
            })
            .catch((error) => {
              console.log("Errore nella ricerca");
              console.log(error);
            })
        },

        searchResponse(criteria){
          console.log(criteria)
          if ((criteria[0] == "All" && criteria[1] == "All")) {
            this.filteredMusics = this.musics

          } else if((criteria[0] == "All" && criteria[1] != "All")){
            this.filteredMusics = this.musics.filter( (music) => music.genre.includes(""));
            this.filteredMusics = this.filteredMusics.filter( (music) =>  music.author.includes(criteria[1]));

          } else if((criteria[0] != "All" && criteria[1] == "All")){
            this.filteredMusics = this.musics.filter( (music) => music.genre.includes(criteria[0]));
            this.filteredMusics = this.filteredMusics.filter( (music) =>  music.author.includes(""));
            
          } else if((criteria[0] != "All" && criteria[1] != "All")){
            
            this.filteredMusics = this.musics.filter( (music) => music.genre.includes(criteria[0]));
            console.log(this.filteredMusics)
            this.filteredMusics = this.filteredMusics.filter( (music) =>  music.author.includes(criteria[1]));
            console.log(this.filteredMusics)
          }
        },

        artistSearchResponse(artistSelected){
          if (artistSelected == "" || artistSelected == "All") {
            this.searchSentinell[1] = true;
            if (this.searchSentinell[0] == true && this.searchSentinell[1] == true) {
              this.filteredMusics = this.musics;
            }
          } else{
            this.searchSentinell[1] = false;
            this.filteredMusics = this.filteredMusics.filter( (music) => music.author.includes(artistSelected));
          }
        },

        testNew(search){
          console.log(search);
        }
    },

    created() {
        this.getElemementFromApi();
    },
    components: {
    MusicCard,
    GenreSearch,
    ArtistSearch,
    SearchItems
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

  .search{
    padding: 20px;
  }
</style>