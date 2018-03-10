<template>
  
<div id="about" style="text-align:center;font-size:1.6em;">

<h1> About </h1>

<p>Hey there, {{ userName }}</p>

</div>

</template>

<script>
    export default {
        data()
        {
            return{
        userName : this.$route.params.name
            }
        }
    }
</script>

<style scoped>

html, body{
    height: 100%;
    margin: 0;
    padding: 0;
}

#about{
    margin-bottom: 450px;
}


</style>

