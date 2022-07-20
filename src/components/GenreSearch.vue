<template>
    <form>
        <div class="form-floating">
            <select class="form-select" id="floatingSelect" aria-label="Floating label select example" v-model="genreSelected"
            @change="$emit('search', genreSelected)">
                <option :value="genre" v-for="(genre, index) in genres" :key="index" >
                    {{ genre }}
                </option>

                <option value="All">All</option>
            </select>
            <label for="floatingSelect">Select the genre to search for</label>
        </div>

        <!-- <a href="#" class="btn btn-primary" @click.prevent="$emit('search', genreSelected)">Prova</a> -->
    </form>
</template>

<script>
export default {
    data: function(){
        return{
            genreSelected: "",
            test: "send",
        }
    },

    props:{
        genres:{
            type: Array,
            required: true,
        }
    },

    methods:{
        log(){
            console.log(this.genreSelected)
        }
    },
}
</script>

<style lang="scss" scoped>

    .form-floating{
        width: 30%;
    }

</style>