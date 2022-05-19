<template>
  <select 
      v-model="genre"
      @change="$emit('selectGenre',genre)"
      id="genere" class="form-select sd-form">
        <option value ="">Seleziona un genere</option>
        <option 
        v-for="(genre,index) in getFileredArray" :key="`option-${index}`">{{genre}}</option>
        
  </select>
</template>

<script>
export default {
  name: 'SelectGenre',
  props:{ cardArray: Array },

  data() {
    return {
      genre: '',
    };
  },

  computed:{
    getFileredArray(){
      let genreArray = [];
      this.cardArray.forEach(card=>{
        if(!genreArray.includes(card.genre)) genreArray.push(card.genre);
        
      })
      return genreArray;
    }
  }
}
</script>

<style lang="scss" scoped>

</style>