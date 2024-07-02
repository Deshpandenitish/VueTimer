<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
  <h1>{{title}}</h1>
  <!-- <input type="text" ref="name" @click="handleclick">
  <button @click="handleclick">Click</button> -->
  <div v-if="showmodal">
    <Login :header="header" :text="text" theme="" @close="togglemodal">
      <template v-slot:links>
        <button>Sign Up</button>
        <button>More Info</button>
      </template>
      <h1>{{header}}</h1>
      <p>{{text}}</p>
    </Login>
  </div>
  <button @click="togglemodal">Show Modal</button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
// import HelloWorld from './components/HelloWorld.vue';
import Login from './components/Login.vue';

export default defineComponent({
  // name:"App",
  components:{Login,},
  data(){
    return {
      title:'Vue App :)',
      header:'Sign up for give away!',
      text:'Grab you stufs for half price',
      showmodal:false,
      name:'',
    }
  },
  methods:{
    handleclick(){
      console.log(this.$refs.name);
    },
    togglemodal(){
      this.showmodal=!this.showmodal;
    },
  }
  // name: 'App',
  // components: {
  //   HelloWorld
  // }
});
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
