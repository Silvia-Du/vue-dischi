<template>
  <div>
    <HeaderComp />
    <MainComp />
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
      
    }
  },

  methods: {
    selectForGenre(cardGenre){
      console.log(cardGenre);
    }
  }
}
</script>

<style lang="scss">

@import './assets/style/vars.scss';
@import './assets/style/mixin.scss';
@import './assets/style/general.scss';


</style>
