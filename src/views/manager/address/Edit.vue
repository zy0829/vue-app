<template>
    <briup-fulllayout title="新增地址">
    <div>
    <van-cell-group>
        <van-field v-model="form.telephone" placeholder="请输入手机号" />
    </van-cell-group>
    <van-cell-group>
        <van-field v-model="form.province" placeholder="省份" />
    </van-cell-group>
    <van-cell-group>
        <van-field v-model="form.city" placeholder="市" />
    </van-cell-group>
    <van-cell-group>
        <van-field v-model="form.area" placeholder="区" />
    </van-cell-group>
    <van-cell-group>
        <van-field v-model="form.address" placeholder="请输入详细地址" />
    </van-cell-group>
    <van-button block type="primary" @click="submitHandler">保存</van-button>
    </div>    
    </briup-fulllayout>
</template>
<script>
import {mapState} from 'vuex'
import {post}  from '../../../http/axios'
export default {
    methods:{
        submitHandler(){
            let url="address/saveOrUpdate"
            this.form.customerId=this.info.id
            post(url,this.form).then((response)=>{   
                this.$router.go(-1);
                this.$toast.success(response.message);
            })
        }
    },
    data(){
        return{
            form:{}
        }
    },
    computed:{
        ...mapState("user",["info"])
    }
    
}
</script>
<style scoped>

</style>