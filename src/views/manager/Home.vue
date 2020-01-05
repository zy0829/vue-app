<template>
  <div class="home">
    <header class="header">
      <img src="../../assets/home.jpg" alt="">
    </header>
  <div>
    <van-grid :column-num="3">
  <van-grid-item
    v-for="value in categories"
    :key="value.id"
    :icon="value.icon"
    :text="value.name"
  />
</van-grid>
<van-grid :column-num="1" icon-size="300px">
  <van-grid-item
    v-for="value in products"
    :key="value.id"
    :icon="value.photo"
    :text="value.name"
  />
</van-grid>
  </div>
   
  </div>
</template>
<script>
import {get,post} from '../../http/axios';
export default {
  data(){
  return{ 
    categories:[],
    products:[] 
  } 
  },
  
  created(){
    this.loadCategories();
    this.loadProduct();
  },
  methods:{
    //加载栏目信息
  loadCategories(){
    let url="/category/findAll";
    get(url).then((response)=>{
      this.categories=response.data.slice(0,6);
    })
},
loadProduct(){
  //加载产品信息
  let url="/product/query"
  let params={
    page:0,
    pageSize:10
  }
  post(url,params).then((response)=>{
    this.products=response.data.list;
  })
}
  }
}
</script>
<style scoped>
.home {
  padding-bottom: 50px;
}
.header {
  height: 300px;
  overflow: hidden;
}
.header img {
  width: 100%;
}
</style>