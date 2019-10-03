<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png">
    </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
// 错误处理:请求错误时处理
export default {
    name: 'axios3-4',
    created () {
        axios.interceptors.request.use(
            config =>{
                return config
            },
            err =>{
                return Promise.reject(err)
            }
        )
        axios.get('/data.json').then(res => {
            console.log(res)
        }).catch(err => {
            console.log(err)
        })

        //例子，在实际开发中，一般添加统一错误处理
        let instance = axios.create({})
        instance.interceptors.request.use(
            config => {
                return config
            },
            err => {
                //请求错误，http状态码一般以4开头
                //401:超时
                //404:找不到资源
                $('#model').show()
                setTimeout(()=>{
                    $('#model').hide()
                },2000)
                return Promise.reject(err)
            }
        )
        instance.interceptors.response.use(
            res => {
                return res
            },
            err => {
                //响应错误，一般http状态码5开头
                //500:服务器错误
                $('#model').show()
                setTimeout(()=>{
                    $('#model').hide()
                },2000)
                return Promise.reject(err)
            }
        )
        instance.get('/data.json').then(res => {
            console.log(res)
        })
    },
}
</script>
