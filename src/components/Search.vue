<template>
    <div id="container">   
    <a-row type="flex"  class="demo" justify="center" >
      <a-col :span="6" >
        <span>GITHUB SEARCH</span>
      </a-col>
      <a-col :span="18" >
       <a-input-search placeholder="input user" style="width: 200px" @search="onSearch()" v-model="keyword" />
      </a-col>
    </a-row>
  </div>

</template>
<script>
import axios from 'axios'
export default {
    name:'Search',
    data(){
        return{
            keyword:'',

        }
    },
    methods:{
        onSearch(){
            this.$bus.$emit('userInfo',{user:[],loading:true,spining:true,errMessage:"",isHome:false})
            // console.log("search");
            // console.log(this.keyword);
            // axios.get(`https://api.github.com/search/users?q=${this.keyword}`)
            axios.get('https://api.github.com/search/users?',{
                params:{
                    q:this.keyword
                    
                }
                }).then((res) => {
                this.$bus.$emit('userInfo',{user:res.data.items,laoding:true,spining:false,errMessage:""})
                this.$message.success('sccess search',1);
                // console.log(res.data.items);
                // this.user=res.data.items;
                 
                // console.log(this.user);
                
            }).catch((err) => {
                this.$message.error(err.message,
                1,
                );
                this.$bus.$emit('userInfo',{user:'',laoding:false,spining:false,errMessage:err.message,isErr:true})
                console.log(err.message);
                
            });
         
        }
    }
    

}
</script>

<style scoped>
#container{
    justify-content: center;
    align-items: center;
}
.demo{
    color: #EEE;
    display: flex;
    background:#a2d2ff;
    height: 50px;
    align-items: center;
}

</style>