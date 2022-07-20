<template>
    <form>
        <div class="form-floating">
            <select class="form-select" id="floatingSelect" aria-label="Floating label select example" v-model="genreSelected" @click="genreItems">
                <option :value="index" v-for="(genre, index) in genres" :key="index">
                    {{ genre }}
                </option>
            </select>
            <label for="floatingSelect">Select the genre to search for</label>
        </div>
    </form>
</template>

<script>
export default {
    data: function(){
        return{
            genreSelected: "",
            genres: [],
        }
    },

    props:{
        allMusics:{
            type: Array,
            required: true,
        }
    },

    methods:{
        log(musics){
            console.log(musics);
        },

        genreItems(){
            for (let index = 0; index < this.allMusics.length; index++) {
                if (this.genres.includes(this.allMusics[index].genre) == false) {
                    this.genres[index] = this.allMusics[index].genre;
                    console.log(this.genres[index])
                    console.log(this.allMusics[index].genre)
                }
            }
            console.log(this.genres);
        }
    },
}
</script>

<style lang="scss" scoped>

    .form-floating{
        width: 30%;
    }

</style>