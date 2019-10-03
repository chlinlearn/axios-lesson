<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
export default {
  name: 'axios2-2',
  components: {
  },
  //http://localhost:8080/data.json?id=12
  created () {
    axios.get('/data.json',{
        params : {
            id:2
        }
    }).then((res) => {
      console.log(res)
    })
    axios({
        method : 'GET',
        url : '/data.json',
        params : {
            id : 2
        }
    }).then((res) => {
        console.log(res)
    })
    //post
    // form-data 表单提交
    // applicaton/json
    let data = {
        id : 3
    }
    axios.post('/post',data).then((res) => {
        console.log(res)
    })
    axios({
        method: "POST",
        url: '/post',
        data: data
    }).then((rse) => {
        console.log(res)
    })
  }
}
</script>
