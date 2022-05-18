<template>

  <main class="d-flex align-items-center justify-content-center py-3">
    <div 
    v-if="isLoading"
    class="container">
      <div class="sd-row row d-flex justify-content-center">
        <CardItem
        v-for="(card, index) in CardsListForGenre" :key="`card-${index}`" 
        :cardItem="card"/>
      </div>
    </div>
    <div v-else><LoadingComp :loadingMsg="`Ci siamo quasi!`"/></div>
  </main>

</template>

<script>

import CardItem from './CardItem.vue';
import axios from 'axios';
import LoadingComp from './LoadingComp.vue';

export default {
    name: "MainComp",
    props: { selectedGenre: String },
    components: { CardItem, LoadingComp },

    computed:{

      CardsListForGenre(){
        let listForGenre = [];
        if(this.selectedGenre === ''){
          listForGenre = this.cardsList;
        }else{
          listForGenre = this.cardsList.filter(card =>{
            return card.genre === this.selectedGenre;
          })
        }
        return listForGenre;
      }
    },


    data(){
      return{
        apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
        cardsList :[],
        isLoading: false,
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
          this.isLoading = true;
        })
        .catch(error => {
          console.log(error);
        })
      }
    },

}
</script>

<style lang="scss" scoped>

  main{
    min-height: calc(100vh - 80px);
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