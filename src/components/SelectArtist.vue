<template>
  <input 
  v-model.trim="getArtist"
  @keyup="$emit('selectedArtist', getArtist)"
  type="text" class="form-control me-2" placeholder="Cerca per Artista">
</template>

<script>
export default {
  name: 'selectArtist',

  data(){
    return{
      getArtist:'',
    }
  }
}
</script>

<style>

</style>