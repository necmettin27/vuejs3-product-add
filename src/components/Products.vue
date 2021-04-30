<template>
    <div v-if="productlist.length>0">
      <h3 class="text-center">Eklenen Ürünlerin Listesi</h3>
        <hr>
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
        if(this.productlist.length < 10){
          this.productlist.push(product)
          
          emitter.emit("ProgressUpdate",this.productlist.length);

        }else{
          alert("Daha fazla ürün ekleyemezsiniz.")
        }
        
      });
    }
}
</script>