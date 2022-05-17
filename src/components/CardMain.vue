<template>

    <div class="_card text-center">
      <img :src="cardItem.poster" :alt="cardItem.title">
      <p>{{cardItem.title}}</p>
      <p class="mb-0">{{cardItem.author}}</p>
      <p>{{cardItem.year}}</p>
    </div>
  
</template>

<script>
export default {
  name: 'CardMain',
  props: {cardItem: Object}
}
</script>

<style lang="scss" scoped>

  @import '../assets/style/vars.scss';

  ._card{
    background-color: $lightenColor;
    padding: 15px;
    margin: 0 15px 30px 15px;
    width: calc((100% / 5) - 30px);

    & p:first-of-type{
      color: white;
      font-size: 0.9rem;
      text-transform: uppercase;
    }
    p{
      color: #716f6f;
    }
    img{
      width: 100%;
      margin-bottom: 10px;
    }
  }

</style>