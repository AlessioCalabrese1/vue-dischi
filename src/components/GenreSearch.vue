<template>
    <form>
        <div class="form-floating">
            <select class="form-select" id="floatingSelect" aria-label="Floating label select example" v-model="genreSelected">
                <option :value="index" v-for="(genre, index) in genres" :key="index" @click="$emit('search', index)">
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