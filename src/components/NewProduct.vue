<template>
     <div class="row">
      <div class="card offset-2 col-md-3">
        <div class="card-body tex-center d-flex align-items-center flex-column">
          <img height="128" class="img-responsive text-center mb-3"
               :src="product.selectedImage == null ? defaultimage : product.selectedImage">
          <input ref="file" type="file" style="display: none;" @change="onChange($event)" class="form-control">
          <button class="btn btn-outline-secondary " type="button" @click="$refs.file.click()">Resim Seç</button>
        </div>
      </div>
      <div class="col-md-5">
        <div class="col-md-11 card">
          <div class="card-body">
            <div class="form-group">
              <label>Ürün Adı</label>
              <input type="text" v-model="product.title" class="form-control" placeholder="adını giriniz">
            </div>
            <div class="row">
              <div class="form-group col-md-6">
                <label>Ürün Adeti</label>
                <input type="text" v-model="product.count" class="form-control" placeholder="adetini giriniz">
              </div>
              <div class="form-group col-md-6">
                <label>Ürün Fiyatı</label>
                <input type="text" v-model="product.price" class="form-control" placeholder="fiyatını giriniz">
              </div>
            </div>
            <button @click="addProduct" class="btn btn-outline-info btn-block">Ekle!</button>
          </div>
        </div>
      </div>
    </div>
</template>
<script>
import emitter from 'tiny-emitter/instance'
export default {
    data(){
        return{
          defaultimage : require('@/assets/default.png'),
            product : {
                selectedImage: null,
                title : null,
                count : null,
                price : null,
                totalprice : null

            }
        }
    },
     methods: {
      onChange(e) {
        const file = e.target.files[0];
        this.product.selectedImage = URL.createObjectURL(file);
      },
      addProduct(){
        this.product.totalprice = this.product.count * this.product.price
        emitter.emit('ProductAdded',this.product)
        this.product = {
                selectedImage: null,
                title : null,
                count : null,
                price : null,
                totalprice : null

            }
      }
    }
}
</script>