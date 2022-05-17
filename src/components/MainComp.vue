<template>

  <main>
    <div class="container debug">
      <div class="sd-row row debug d-flex justify-content-center">
        
        <CardMain />
        
      </div>
    </div>
  </main>

</template>

<script>
import CardMain from './CardMain.vue';
export default {
    name: "MainComp",
    components: { CardMain }
}
</script>

<style lang="scss" scoped>

  main{
    padding: 70px 0;
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