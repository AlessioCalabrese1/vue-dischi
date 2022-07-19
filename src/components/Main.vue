<template>
  <div>
    <MusicCard v-for="(music, index) in musics" :key="index"
      :music=music
    />
  </div>
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

<style>

</style>