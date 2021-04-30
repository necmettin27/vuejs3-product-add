<template>
  <div class="container">
    <h1 class="text-center">Ürün Ekleme Uygulaması</h1>
    <hr>
    <app-NewProduct></app-NewProduct>
    <br><br>
      <app-Progress></app-Progress>
    <br><br>
   
    <app-Products></app-Products>

  </div>


</template>


<script>
import Products from './components/Products'
import NewProduct from './components/NewProduct'
import Progress from './components/Progress'
export default {
  name: 'App',
  components: {
    appProducts : Products,
    appNewProduct : NewProduct,
    appProgress : Progress,
  },
  data() {
      return {
       
      }
    }
}
</script>

<style>
 body {
    background-color: aliceblue;
    padding-top: 20px;
    padding-bottom: 20px;
  }

  .card{
    margin-right: 5px;
    margin-bottom: 5px;
  }

  .card:last-child{
    margin-right: 0px;
  }

  .col-md-2{
    max-width: 15.666667%!important;
  }

  .product-container{
    margin-left: 15px;
  }
</style>
