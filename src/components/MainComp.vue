<template>

  <main class="d-flex align-items-center">
    <div class="container">
      <div class="sd-row row d-flex justify-content-center">
        
        <CardMain 
        v-for="(card, index) in cardsList" :key="`card-${index}`" 
        :cardItem="card"/>
      </div>
    </div>
  </main>

</template>

<script>

import CardMain from './CardMain.vue';
import axios from 'axios';

export default {
    name: "MainComp",
    components: { CardMain },

    data(){
      return{
        apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
        cardsList :[],
      }
    },

    
    mounted() {
      this.getDataDiscs();
    },

    methods:{
      getDataDiscs(){
        axios.get(this.apiUrl)
        .then(response => {
          this.cardsList = response.data.response;
          
        })
      }
    },

}
</script>

<style lang="scss" scoped>

  main{
    height: calc(100vh - 80px);
    background-color: #1e2d3b;
    .sd-row{
      margin: 0 auto;
      flex-wrap: wrap;
      width: 100%;
      .col{
        margin: 5px;
      }
    }
  }
</style>