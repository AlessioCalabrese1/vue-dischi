<template>
  <main>
    <div class="musics-card-container container">
      <div class="row g-2">
        <MusicCard v-for="(music, index) in musics" :key="index"
        :musicElement="music"
        />
      </div>
        
    </div>
    
  </main>
</template>

<script>
import axios from 'axios';
import MusicCard from "./MusicCard.vue";

export default {
    
    data: function(){
      return{
        musics: [],
      }
    },

    methods: {
        getElemementFromApi() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((result) => {
              this.musics = result.data.response;
              console.log(this.musics)
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
      MusicCard 
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
</style>