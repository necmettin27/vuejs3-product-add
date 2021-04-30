<template>
    <div class="row product-container">
      <app-product v-for="product in products" :key="product.id">
        <img class="card-img-top" :src="defaultimage" alt="Card image cap">
        <div class="card-body">
          <h5 class="card-title">Card title</h5>
          <small>
            <strong>Adet : </strong> 1
          </small>
          <br>
          <small>
            <strong>Fiyat : </strong> 10
          </small>
          <br>
          <small>
            <strong>Tutar : </strong> 10
          </small>
        </div>
      </app-product>
    </div>
</template>
<script>
import Product from './Product'
export default {
  components : {
    appProduct : Product
  },
  data(){
      return{
        defaultimage : require('@/assets/default.png'),
         productlist: [],
      }
    }
}
</script>