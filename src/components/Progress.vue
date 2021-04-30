<template>
   <div class="progress">
      <div class="progress-bar bg-info" role="progressbar" :style="{width: this.progress+'%'}" aria-valuenow="50" aria-valuemin="50" aria-valuemax="100">
        {{currentItem}}/10
      </div>
    </div>
</template>
<script>
import emitter from 'tiny-emitter/instance'

export default {
  data() {
    return {
      currentItem : 0,
      progress : 0
    }
  },
  created(){
    emitter.on("ProgressUpdate",(productListCount)=>{
      this.currentItem = productListCount;
      this.progress = productListCount*10;
    })
  }
}
</script>