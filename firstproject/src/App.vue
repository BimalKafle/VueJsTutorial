
<template>
  <img alt="Vue logo" src="./assets/logo.png">

   <FeatureTemplate :num="num" @update:num="updateNum"/>
   
   <HelloWorld msg="Welcome to Your Vue.js App"/>


</template>
 

<script>
import HelloWorld from './components/HelloWorld.vue'
import FeatureTemplate from './components/Template.vue'


export default {
  name: 'App',
  components: {
    HelloWorld,
    FeatureTemplate
  },
  data() {
    return {
      num: 0
    };
  },
  methods: {
    updateNum(updatedNum) {
      this.num = updatedNum; // Update the prop value in the parent component
    }
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
  margin-top: 60px;
}
</style>
