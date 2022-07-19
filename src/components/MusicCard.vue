<template>
  <div>
    {{musicElement.title}}
  </div>
</template>

<script>
export default {
    props:{
        musicElement:{
            type: Object,
            required: true,
        }
    }
}
</script>

<style>

</style>