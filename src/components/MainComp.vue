<template>

  <main class="d-flex align-items-center justify-content-center py-3">
    <div 
    v-if="isLoading"
    class="container">
      <div class="sd-row row d-flex justify-content-center">
        <CardItem
        v-for="(card, index) in listToPrint" :key="`card-${index}`" 
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

    props: { 
      selectedGenre: String,
      selectedArtist: String
    },

    components: { CardItem, LoadingComp },

    data(){
      return{
        apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
        cardsList :[],
        listForArtist:[],
        isLoading: false,
      }
    },

    computed:{

      listToPrint(){
        let fileterdList = [];

        if(this.selectedGenre != ''){
          fileterdList = this.cardsList.filter(card => card.genre === this.selectedGenre);
        }else{
          fileterdList = this.cardsList;
        }

        if(this.selectedArtist != ''){
          let doubleCheckList =[];
          doubleCheckList = fileterdList.filter(card => card.author.toLowerCase().includes(this.selectedArtist.toLowerCase()))

          fileterdList = doubleCheckList;
        }
        return fileterdList;
      }

    },

    //chiamata axios
    mounted(){
      this.getDataDiscs();
    },

    methods:{

      getDataDiscs(){
        axios.get(this.apiUrl)
        .then(response => {
          this.cardsList = response.data.response;
          this.isLoading = true;

          const genreList =[];
          this.cardsList.forEach(card => {

            if(!genreList.includes(card.genre)){
              genreList.push(card.genre);
            }
          });
          this.$emit('getSelectOption', genreList);
          
        })
        .catch(error => {
          console.log(error);
        })
      },

    }

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