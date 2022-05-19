<template>
  <select 
      v-model="genre"
      @change="$emit('selectGenre',genre)"
      id="genere" class="form-select sd-form">
        <option value ="">Seleziona un genere</option>
        <option 
        v-for="(genre,index) in optionArray" :key="`option-${index}`">{{genre}}</option>
        
  </select>
</template>

<script>
export default {
  name: 'SelectGenre',
  props:{ optionArray: Array },

  data() {
    return {
      genre: '',
    };
  }
}
</script>

<style lang="scss" scoped>

</style>