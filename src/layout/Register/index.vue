<template>
    <div class="register">

        <div style="color:#666">注册账号</div>
        <div class="box">

            <el-form label-position="top" label-width="100px" :model="register" ref="regFormRef" :rules="regFormRule">
                <el-form-item label="用户名" prop="username">
                    <el-input v-model="register.username" />
                </el-form-item>
                <el-form-item label="密码" prop="password">
                    <el-input v-model="register.password" type="password" />
                </el-form-item>
                <el-form-item label="确认密码" prop="repassword">
                    <el-input v-model="register.repassword" type="password" />
                </el-form-item>
                <el-form-item label="昵称" prop="nickname">
                    <el-input v-model="register.nickname" />
                </el-form-item>
                <el-form-item label="性别" prop="gender">
                    <el-radio-group v-model="register.gender" class="ml-4">
                        <el-radio label="0" size="large">女</el-radio>
                        <el-radio label="1" size="large">男</el-radio>
                    </el-radio-group>
                </el-form-item>
                <el-form-item label="手机" prop="phone">
                    <el-input v-model="register.phone" />
                </el-form-item>

                <el-form-item>
                    <el-button type="primary" @click="submitReg">注册</el-button>
                    <el-button type="info" @click="reset">重置</el-button>
                </el-form-item>

            </el-form>
        </div>
    </div>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue'
import { useUser } from '../../stores/useLogin'
import { ElMessage } from 'element-plus'
import { useRouter } from 'vue-router'
import axios from 'axios'

const router = useRouter()
const User = useUser()

const register = reactive({
    id: '',
    username: '',
    password: '',
    repassword: '',
    gender: 0,
    phone: '',
    email: '',
    nickname: ''
})

const reset = () => {
    register.username = ''
    register.password = ''
    register.repassword = ''
    register.email = ''
    register.nickname = ''
    register.gender = 0
    register.phone = ''
}

const regFormRef = ref()

//表单完整规则
const regFormRule = reactive({
    username: [
        { required: true, message: '请输入用户名', trigger: 'blur' },
        { min: 2, max: 10, message: '长度在2到10之间', trigger: 'blur' },
    ],
    password: [
        { required: true, message: '请输入密码', trigger: 'blur' },
        { min: 5, max: 15, message: '长度在5到15之间', trigger: 'blur' },
    ],
    repassword: [
        { required: true, message: '请确认密码', trigger: 'blur' },
        { min: 5, max: 15, message: '长度在5到15之间', trigger: 'blur' },
    ],
    phone: [
        { required: true, message: '请输入手机号', trigger: 'blur' }
    ],
    gender: [
        { required: true, message: '请输入性别', trigger: 'blur' }
    ],
    nickname: [
        { required: true, message: '请输入昵称', trigger: 'blur' }
    ]
})

//用户信息
const user = reactive({
    list: []
})


const submitReg = () => {

    getUserList()

    let status = 0

    user.list.forEach(item => {
        if (item.username == register.username || item.id == register.username) {
            status = 1
        }
    })

    if (status == 0) {
        axios({
            url: 'http://123.60.44.50:3000/users',
            method: 'post',
            data: {
                id: register.username,
                username: register.username,
                password: register.password,
                phone: register.phone,
                gender: register.gender,
                nickname: register.nickname
            }
        }).then(res => {

            ElMessage.success('注册成功，换一个用户名吧')

            router.push({path:'/login'})
        }).catch(err => {
            ElMessage.error('注册失败，服务器存在问题')
        })
    }else{
        ElMessage.error('该用户名已存在')
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

</script>

<style scoped lang='less'>
.register {
    width: 100%;
    height: 800px;
    background-color: #fff;
    margin-top: 10px;
    display: flex;
    flex-flow: column;
    align-items: center;
    padding: 30px;

    .box {
        margin-top: 20px;
        width: 500px;
        padding: 20px;
        border: 1px solid #ccc;
    }
}
</style>