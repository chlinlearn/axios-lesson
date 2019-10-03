<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png">
    </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
// 取消请求:取消正在进行的http请求(了解)
export default {
    name: 'axios3-5',
    created () {
        let source = axios.CancelToken.source()
        axios.get('/data.json',{
            cancelToken:source.token
        }).then(res => {
            console.log(res)
        }).catch(err =>{
            console.log(err)
        })

        //取消请求
        source.cancel('cancel http')

        //例子，查询时长时间没有响应进行取消请求
        
    },
}
</script>
