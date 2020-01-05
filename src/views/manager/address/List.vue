<template>
    <briup-fulllayout title="常用地址">
<van-list>
  <van-cell
    v-for="item in address"
    :key="item.id"
    :title="item.province+' '+item.city+' '+item.area+' '+item.address"
  />
</van-list>
<br>
<van-button block type="default" color="red" @click="toAddressEditHandler">新增地址</van-button>
</briup-fulllayout>
 
</template>

<script>
import {get} from '../../../http/axios'
import {mapState} from 'vuex'
export default {
    data(){
        return{
            address:[]
        }
    },
    created(){
        this.loadaddress();

    },
    computed:{
        ...mapState("user",["info"])
    },
    methods:{
        toAddressEditHandler(){
            this.$router.push("/manager/edit")
        },
        loadaddress(){
            let id=this.info.id;
            let url="/address/findByCustomerId?id="+id;
            get(url).then((response)=>{
                this.address=response.data;
            })
        }

    }
    
}
</script>
<style  scoped>

</style>