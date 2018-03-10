<template>
  <div id="app">
    <nav>

      <router-link to="/"> Home </router-link>
      <router-link to="/about"> About </router-link>
    </nav>  
      <router-view/>
  </div>
</template>

<script>
import Skills from './components/Skills.vue'

export default {
  name: 'app',
  components: {
    Skills
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Montserrat:400,700');
  @import url('https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.5.2/animate.css');
  @import url('https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css');
  
body {
    background-color: #eeeeee;
  font-family: 'Montserrat', sans-serif;
}
#app {
 margin-top: 50px;   
}

nav{
  display: inline-block;
  margin-left: 240px;
}

nav>a{
  text-decoration: none;
  border: 3px solid #fff;
  background: #293;
  padding: 10px;
  font-size: 25px;
  color: #fff;
  border-radius: 8px;
  transition: 0.4s all ease-in-out;
}

nav>a:hover{
  background-color: #fff;
  color: #293;
  border-color: #293;
}
</style>
