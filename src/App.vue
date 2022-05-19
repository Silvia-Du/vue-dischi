<template>
  <div>
    <HeaderComp :optionList="optionListToSend" @getGenreEvent ="filteredByGenre" @getArtistEvent ="filteredByArtist"/>
    <MainComp :selectedGenre="cardType" :selectedArtist= "cardArtist" @getSelectOption="getSelectOption"/>
  </div>
</template>

<script>
import HeaderComp from "./components/HeaderComp.vue";
import MainComp from "./components/MainComp.vue";



export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },

  data() {
    return {
      cardType: '',
      cardArtist: '',
      optionListToSend: [],
    }
  },

  methods: {
    filteredByGenre(cardGenre){
      // console.log('ascotatore 2');
      this.cardType = cardGenre;
    },

    filteredByArtist(artistString){
      // console.log('ascoltatore 2 artist');
      this.cardArtist = artistString;
      console.log(artistString);
    },

    getSelectOption(optionList){
      this.optionListToSend = optionList;
    }


  }
}
</script>

<style lang="scss">

@import './assets/style/vars.scss';
@import './assets/style/mixin.scss';
@import './assets/style/general.scss';


</style>
