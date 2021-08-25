<template>
 <div id="list">
       <a-spin :spinning="info.spining"
               tip="loading···"
             class="demo1">
           <a :href="item.html_url" target="_blank" class="demo"  v-for="item in info.user" :key="item.id">
    <a-card hoverable activeTabKey v-for="item in info.user" :key="item.id"  style="width:25%;margin:10px"  :loading="info.loading">
        <img
      style="padding:10px"
      slot="cover"
      alt="example"
      :src=item.avatar_url
    />
     <a-card-meta :title=item.login>
    </a-card-meta>
    </a-card>
           </a>
       </a-spin>
  <a-result status="404" :title="info.errMessage"  v-show="info.isErr">
    <template #extra>
      <a-button key="console" type="primary" @click="refresh">
        please input again
      </a-button>
    </template>
  </a-result>
    </div>
</template>
<script>
export default {
    name:'List',
    data(){
        return{
           info:{
            user:[],
            loading:false,
            spining:false,
            errMessage:'',
            isErr:false
           }
        }
    },
    methods:{

    },
    mounted(){
        this.$bus.$on('userInfo',(dataObj)=>{
        //    this.info=dataObj;
        this.info= {...this.info,...dataObj}
           console.log(dataObj);
        })
   
}
}

</script>
<style scoped>
.demo{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
}
.demo1{
    margin-top:100px ;
}

</style>