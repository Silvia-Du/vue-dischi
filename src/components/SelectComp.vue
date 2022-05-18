<template>
  <select 
      v-model="genre"
      @change="$emit('selectGenre',genre)"
      id="genere" class="form-select sd-form">
        <option selected>Seleziona un genere</option>
        <option value="Rock">Rock</option>
        <option value="Pop">Pop</option>
        <option value="Jazz">Jazz</option>
        <option value="Metal">Metal</option>
  </select>
</template>

<script>
export default {
  name: 'SelectComp',

   data() {
        return {
            genre: "Seleziona un genere"
        };
    },

    methods:{
      
    }
}
</script>

<style lang="scss" scoped>

</style>