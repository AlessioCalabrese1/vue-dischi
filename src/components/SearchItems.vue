<template>
    <div>
        <GenreSearch :genres="genres" @searchGenre="getGenre" />

        <ArtistSearch :artists="artists" @searchArtist="getArtist" />

        <a href="#" @click.prevent="$emit('principal', searchCriteria)">Cerca</a>
    </div>
</template>

<script>
import GenreSearch from './GenreSearch.vue';
import ArtistSearch from './ArtistSearch.vue';
export default {
    props: {
        genres: {
            type: Array,
            required: true
        },
        artists: {
            type: Array,
            required: true
        }
    },

    data: function(){
        return{
            searchCriteria: ["All", "All"],
        }
    },

    methods:{
        getGenre(genre){
            this.searchCriteria[0] = genre;
        },

        getArtist(artist){
            this.searchCriteria[1] = artist;
        }
    },  

    components: { GenreSearch , ArtistSearch}
}
</script>

<style>

</style>