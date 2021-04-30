<template>
    <div class="row product-container">
      <app-product v-for="product in productlist" :key="product.id">
        <img class="card-img-top" :src="product.selectedImage" alt="Card image cap">
        <div class="card-body">
          <h5 class="card-title">{{product.title}}</h5>
          <small>
            <strong>Adet : </strong> {{product.count}}
          </small>
          <br>
          <small>
            <strong>Fiyat : </strong> {{product.price}}
          </small>
          <br>
          <small>
            <strong>Tutar : </strong> {{product.totalprice}}
          </small>
        </div>
      </app-product>
    </div>
</template>
<script>
import emitter from 'tiny-emitter/instance'
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
  },
  created() {
      emitter.on('ProductAdded', (product) => {
        this.productlist.push(product)
      });
    }
}
</script>