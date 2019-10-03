<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
// axios实例
// 后端接口地址有多个，并且超时时长不一样
export default {
  name: 'axios3-1',
  created () {
      let instance = axios.create({
          baseURL: 'http://localhost:8080',
          timeout: 1000
      })
      let instance2 = axios.create({
          baseURL: 'http://localhost:8080',
          timeout: 2000
      })
      instance.get('/data.json').then(res => {
          console.log(res)
      })

      
  }
}
</script>
