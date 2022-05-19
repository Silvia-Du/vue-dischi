<template>
    
    <div class=" text-center col-6 col-md-4 col-lg-2">
      <img  class="img-fluid mb-3" :src="cardItem.poster" :alt="cardItem.title">
      <p>{{cardItem.title}}</p>
      <p class="mb-0">{{cardItem.author}}</p>
      <p>{{cardItem.year}}</p>
    </div>
  
</template>

<script>
export default {
  name: 'CardItem',
  props: {cardItem: Object}
}
</script>

<style lang="scss" scoped>

  @import '../assets/style/vars.scss';

  .col-6{
    background-color: $lightenColor;
    padding: 15px;
    margin: 0 15px 30px 15px;

    & p:first-of-type{
      color: white;
      font-size: 0.9rem;
      text-transform: uppercase;
    }
    p{
      color: #716f6f;
    }
  }

</style>