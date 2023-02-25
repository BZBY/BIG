<template>
    <div class="side">
        <div class="sort">Newest　～　ｂｌｏｇ</div>
        <ul class="list">
            <li v-for="item in topList.list" :key="item.id" @click="toDetial(item.id)">
                <div class="title">{{ item.title }}</div>
                <div class="time">{{ moment(item.createTime).format('YYYY-MM-DD') }}</div>
            </li>
        </ul>
    </div>
</template>

<script setup>
import { ref, reactive,onMounted } from 'vue'
import { top } from '../assets/data/articleData'
import moment from 'moment'
import { useRouter } from 'vue-router'

const router = useRouter()
const topList = reactive({
    list:[]
})

//文章详情页
const toDetial = (id) => {
    router.push({path:'/articleDetial',query:{id:id}})
}

onMounted(()=>{
    topList.list = top
})

</script>

<style scoped lang='less'>
.side{
    width: 100%;
    .sort{
        color:#555;
        font-weight: bold;
        padding:5px 0;
        border-bottom: 2px solid #f2f2f2;
    }

    .list{
        background-color: #f9f9f9;
        padding:10px;
        cursor: pointer;
        li{
            padding:20px 0;
            color:#333;
            border-bottom: 1px solid #e6e6e6;
            .title{
                font-size: 18px;
                overflow: hidden;
                white-space: nowrap;
                text-overflow: ellipsis;
            }

            .time{
                margin-top: 5px;
                font-size: 14px;
                color:#666;
                text-align: end;
            }
        }
    }
}
</style>