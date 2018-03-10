<template>
  <div id="wrapper">
 
  <div id="skills">

    <form @submit.prevent="addSkills">

      <input type="text" v-model="skill" name="skill" placeholder="Enter your skills here..." v-validate="'alpha_dash|required|min:5'">
       
       <transition name="alert" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
        <p class="alert" v-if="errors.has('skill')"> {{ errors.first('skill') }}  </p> 
        </transition>
    </form>

        <ul>
              <transition-group name="skillsets" enter-active-class="animated lightSpeedIn" leave-active-class="animated lightSpeedOut">
              <li v-for="(data, index) in skills" :key='index'> {{ data.niche }} <i class="fa fa-minus-circle" v-on:click="remove(index)"></i></li>
              </transition-group>
        </ul>

        <p v-if="skills.length>=1"> These are your skills. </p>

        <p v-else> Hey, Add your skills! </p>

    </div>

  </div>

</template>

<script>
export default {
  name: 'Skills',
data(){
  return{
    name : 'Skills',

    skills: [
      
      {'niche' : 'React JS'},

      {'niche' : 'Django'},

      {'niche' : 'React Native'}

    ]
    
  }
},
methods:{
addSkills(){
  
  this.$validator.validateAll().then((result) =>{
if(result)
  {
  this.skills.push({niche : this.skill})
  this.skill=""
  }
  else
  {
    console.log("Invalid!")
  }
  })
},
remove(id){
  this.skills.splice(id, 1)
}
} 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

html, body{
  height: 100%;
  outline: none;
  margin: none;
  padding: none;
}

#wrapper{
  height: 100vh;
}

#skills{
  max-width: 750px;
  margin: 30px auto;
  border: 5px solid lightseagreen;
  text-align: center;
  background-color: #e2e0be;
}

.alert{
  background-color: #293;
  padding: 12px;
  width: 70%;
  margin: 30px auto;
  border: 2px solid #fff;
  border-radius: 8px;
  box-shadow: 2px 3px #ccc;
  color: #fff;
  font-family: 'Franklin';
  font-size: 1.7em;
}

ul{
  list-style-type: none;
  text-align: initial;
  padding: 10px;
}

li{
  padding: 10px;
  font-size: 25px;
  background-color: #ccc;
  border-radius: 4px;
  margin: 4px;
  border-left: 6px solid lightcoral;
}

i{
  float:right;
  transition: 0.4s all ease-in-out;
}

i:hover{
  cursor: pointer;
  color: crimson;
}

li>span{
  float:right;
  font-size: 1.4em;
  transition: all 0.4s ease-in-out;
}

li>span:hover{
  color: red;
  font-size: 1.8em;
  cursor: pointer;
}

form{
  padding: 30px;
  outline: none
}

p{
  font-size: 20px;
}

input[type="text"]{
  border: 2px solid lightslategray;
  padding: 20px;
  font-size: 25px;
  width: 50%;
  border-radius: none;
  transition: all 0.4s ease-in-out;
}

input[type="text"]:hover{
  border-radius: 20px;
  border-width: thin;
}

input[type="text"]:focus{
  width: 90%;
}



</style>
