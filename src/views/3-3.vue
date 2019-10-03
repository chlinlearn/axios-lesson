<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png">
    </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
//拦截器：在请求或者响应被处理前拦截
//请求拦截器
//响应拦截器
export default {
    name: 'axios3-3',
    created () {
        //请求拦截器
        axios.interceptors.request.use(config => {
            //在发送请求前做些什么
            return config
        },err => {
            //在请求错误的时候做些什么
            return Promise.reject(err)
        })

        //响应拦截器
        axios.interceptors.response.use(res => {
            //请求成功对响应数据处理
            return res
        },err => {
            //响应错误做些什么
            return Promise.reject(err)
        })

        // axios.get().then((res) => {}).catch((err) => {})

        // 取消拦截器(了解)
        let interceptors = axios.interceptors.request.use(
            config => {
                config.headers = {
                    auth:true
                }
                return config
            }
        )
        axios.interceptors.request.eject(interceptors)

        //例子,登录状态(token:''),需要登录的接口
        let instance = axios.create({

        })
        instance.interceptors.request.use(config => {
            config.headers.token = '' // 建议使用这种方式
            // 会对headers覆盖掉原来的
            // config.headers = {
            //     token:''
            // }
        })

        // 不需要登录的接口
        let newInstance = axios.create({

        })

        //移动端开发
        let instance_phone = axios.create({})
        instance_phone.interceptors.request.use(
            config => {
                //弹窗
                $('#model').show()
                return config
            }
        )
        instance_phone.interceptors.response.use(
            res => {
                //隐藏弹窗
                $('#model').hide()
            }
        )

    }

}
</script>
