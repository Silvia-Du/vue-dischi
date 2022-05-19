<template>
  <select 
      v-model="genre"
      @change="$emit('selectGenre',genre)"
      id="genere" class="form-select sd-form">
        <option selected>Seleziona un genere</option>
        <option 
        v-for="(genre,index) in getFileredArray" :key="`option-${index}`"
        value="Rock">{{genre}}</option>
        <!-- <option value="Pop">Pop</option>
        <option value="Jazz">Jazz</option>
        <option value="Metal">Metal</option> -->
  </select>
</template>

<script>
export default {
  name: 'SelectGenre',
  props:{ cardArray: Array },

  data() {
    return {
      genre: "Seleziona un genere",
    };
  },

  computed:{
    getFileredArray(){
      let genreArray = [];
      this.cardArray.forEach(card=>{
        if(!genreArray.includes(card.genre)){
          genreArray.push(card.genre);
          console.log(genreArray);
        }
      })
      return genreArray;
    }
  }
}
</script>

<style lang="scss" scoped>

</style>