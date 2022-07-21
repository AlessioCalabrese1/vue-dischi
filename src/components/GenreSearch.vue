<template>
    <form>
        <div class="form-floating">
            <select class="form-select" id="floatingSelect" aria-label="Floating label select example" v-model="genreSelected"
            @change="$emit('searchGenre', genreSelected)">
                <option :value="genre" v-for="(genre, index) in genres" :key="index" >
                    {{ genre }}
                </option>

                <option value="All">All</option>
            </select>
            <label for="floatingSelect">Select the genre to search for</label>
        </div>
    </form>
</template>

<script>

export default {
    data: function () {
        return {
            genreSelected: "",
        };
    },
    props: {
        genres: {
            type: Array,
            required: true,
        }
    },
    methods: {
        
    },
}
</script>

<style lang="scss" scoped>

    .form-floating{
        width: 30%;
    }

</style>