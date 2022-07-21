<template>
  <form>
        <div class="form-floating">
            <select class="form-select" id="floatingSelect" aria-label="Floating label select example" v-model="artistSelec"
            @change="$emit('searchArtist', artistSelec)">
                <option :value="artist" v-for="(artist, index) in artists" :key="index" >
                    {{ artist }}
                </option>

                <option value="All">All</option>
            </select>
            <label for="floatingSelect">Select the artist to search for</label>
        </div>
    </form>
</template>

<script>
export default {
    data: function () {
        return {
            artistSelec: "",
        };
    },

    props:{
        artists: {
            type: Array,
            required: true,
        }
    }
}
</script>

<style>
    .form-floating{
        width: 30%;
    }
</style>