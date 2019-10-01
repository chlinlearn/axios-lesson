<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
export default {
  name: 'home',
  components: {
    
  },
  created () {
    axios.get('/data.json').then((res)=>{
      console.log(res);
    })
  }
}
</script>
