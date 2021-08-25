<template>
  <div id="app">
    <search></search>
    <list></list>
    <!-- <demo></demo> -->
    
    
  </div>
</template>

<script>
import List from './components/List.vue'
import Search from './components/Search.vue'
// import Demo from './components/Demo.vue'


export default {
  name: 'App',
  created(){
     this.$notification.open({
        message: 'Notification Title',
        description:
          'welecome to github search',
        icon: <a-icon type="smile" style="color: #108ee9" />,
        placement:"topLeft",
        top:'100px',
      });

  },
  components: {
    Search,
    List,
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
