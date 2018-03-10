<template>
  <div id="wrapper">
 
  <div id="skills">

    <form @submit.prevent="addSkills">

      <input type="text" v-model="skill" name="skill" placeholder="Enter your skills here..." v-validate="'min:5'">
        <p class="alert" v-if="errors.has('skill')"> {{ errors.first('skill') }}  </p> 
    </form>

        <ul>
              
              <li v-for="(data, index) in skills" :key='index'> {{ data.niche }} </li>
        </ul>

        <p> These are your skills. </p>

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
    console.log("In-valid!")
  }
  })
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
  margin: 50px auto;
  border: 5px solid lightseagreen;
  text-align: center;
  background-color: #e2e0be;
}

.alert{
  background-color: #293;
  padding: 12px;
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
