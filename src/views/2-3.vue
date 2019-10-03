<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
//并发请求：同时进行多个请求，并统一处理返回值
export default {
    name: 'axios2-3',
    created () {
        //axios.all() axios.spread()
        axios.all([
            axios.get('/data.json'),
            axios.get('/city.json')
        ]).then(
            axios.spread((dataRes,cityRes) => {
                console.log(dataRes,cityRes)
            })
        )
    }
}
</script>
