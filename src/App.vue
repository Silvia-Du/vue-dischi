<template>
  <div>
    <HeaderComp @getGenre ="FilteredCards"/>
    <MainComp :selectedGenre="cardType"/>
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
    }
  },

  methods: {
    FilteredCards(cardGenre){
      this.cardType = cardGenre;
      console.log(this.cardType,'-----sssss');

    }


  }
}
</script>

<style lang="scss">

@import './assets/style/vars.scss';
@import './assets/style/mixin.scss';
@import './assets/style/general.scss';


</style>
