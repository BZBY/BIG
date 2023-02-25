<template>
    <div class="login">

        <div style="color:#666">登录您的账号以享受全部服务</div>
        <div class="box">

            <el-form label-position="top" label-width="100px" :model="login" style="max-width: 460px">
                <el-form-item label="用户名">
                    <el-input v-model="login.username" />
                </el-form-item>
                <el-form-item label="密码">
                    <el-input v-model="login.password" type="password" />
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" @click="submitLogin">登录</el-button>
                    <el-button type="info" @click="toReg">没有账号</el-button>
                </el-form-item>

            </el-form>
        </div>
    </div>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue'
import { useUser } from '@/stores/useLogin.js'
import { ElMessage } from 'element-plus'
import { useRouter } from 'vue-router'
import axios from 'axios'

const User = useUser()
const router = useRouter()

const user = reactive({
    list: []
})

//登录表单
const login = reactive({
    username: '',
    password: ''
})

//登录
const submitLogin = () => {

    let status = 0 //账号不存在

    if (login.username === '' || login.password === '') {
        ElMessage.error('请正确输入账号密码')
    } else {
        user.list.forEach(item => {
            if (item.username === login.username) {
                if (item.password === login.password) {
                    User.userinfo = item
                    status = 1 //登录成功

                    User.isLogin = true
                    ElMessage.success('登录成功，欢迎您~' + User.userinfo.username)

                    //跳转回上一个页面
                    router.back()

                } else {
                    status = 2 //账号或密码错误
                }
            }
        })

        if (status === 0) {
            ElMessage.error('该账号不存在')
        } else if(status === 2) {
            ElMessage.error('账号或密码错误')
        }

    }
}


//获取用户信息
const getUserList = () => {
    axios({
        url: 'http://123.60.44.50:3000/users',
        method: 'get'
    }).then(res => {
        user.list = res.data
    })
}

//跳转到注册页面
const toReg = () => {
    router.push({ path: '/register' })
}

onMounted(() => {
    getUserList()
})

</script>

<style scoped lang='less'>
.login {
    width: 100%;
    height: 800px;
    background-color: #fff;
  opacity:90%;
    margin-top: 10px;
    display: flex;
    flex-flow: column;
    align-items: center;
    padding: 30px;

    .box {
        margin-top: 20px;
        width: 500px;
        height: 300px;
        padding: 20px;
        border: 1px solid #ccc;
    }
}
</style>