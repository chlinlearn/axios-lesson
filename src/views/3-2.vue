<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png">
    </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
//axios配置参数有哪些
export default {
    name: 'axios3-2',
    created () {
        axios.create({
            baseURL: '',//请求的域名，基本地址
            timeout: 1000,//请求的超时时长(ms)
            url: '/data.json',//请求路径
            method: 'get',//请求方法，get、post、delete、put
            headers: {
                token:''
            },//设置请求头
            params:{},//params会将请求参数拼接到url
            data:{},//data会把参数放在请求体
        })
        axios.get('/data.json').then(res => {
            console.log(res)
        })
            //参数可以在哪些地方配置
            //1.axios全局配置
            axios.defaults.timeout = 1000
            axios.defaults.baseURL = ''
            //2.axios实例配置
            let instance = axios.create({
                baseURL: '',//请求的域名，基本地址
                timeout: 1000,//请求的超时时长(ms)
                url: '/data.json',//请求路径
            })
            //修改实例配置
            instance.defaults.timeout = 2000
            //3.axios请求配置(config)
            instance.get('/data.json',{
                timeout: 5000
            })

            //实际开发
            //有两种请求接口
            //http://localhost:8080
            //http://localhost:8090
            let instance = axios.create({
                baseURL: 'http://localhost:8080',
                timeout: 1000
            })

            let instance2 = axios.create({
                baseURL: 'http://localhost:8090',
                timeout: 3000
            })

            instance.get('/list',
            {
                params:{
                    id:20
                }
            }).then(res => {
                console.log(res)
            })

            instance2.get('/all',{
                timeout: 5000
            }).then(res => {
                console.log(res)
            })
        }

}
</script>
