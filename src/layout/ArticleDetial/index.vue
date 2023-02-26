<template>
    <div class="articleDetial">
        <div class="left">
            <div class="title">
                    {{ article.data.title }}
            </div>
          <div class="time">
<!--            {{ moment(article.data.createTime).format('YYYY年MM月DD日 hh时mm分ss秒') }}-->

          </div>

          <el-button id="copy-btna" type="primary" @click="copyUrl()" style="opacity: 90%; width:32px; height:32px;" >

            <svg t="1677385352434" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2810" width="32" height="32"><path d="M763.84 896c-47.128 0-85.333-38.205-85.333-85.333s38.205-85.333 85.333-85.333c47.128 0 85.333 38.205 85.333 85.333 0 47.128-38.205 85.333-85.333 85.333M329.92 558.848c-14.895 26.231-42.641 43.638-74.453 43.638-47.128 0-85.333-38.205-85.333-85.333 0-16.097 4.457-31.152 12.204-44 14.935-24.769 42.098-41.333 73.13-41.333 47.128 0 85.333 38.205 85.333 85.333 0 15.317-4.035 29.691-11.101 42.117M763.84 128c47.128 0 85.333 38.205 85.333 85.333s-38.205 85.333-85.333 85.333c-47.128 0-85.333-38.205-85.333-85.333 0-47.128 38.205-85.333 85.333-85.333M763.84 682.667c-0.021 0-0.047 0-0.072 0-39.16 0-74.203 17.626-97.628 45.378l-289.885-167.063c4.932-13.101 7.787-28.245 7.787-44.055 0-0.105 0-0.209 0-0.314 0-0.072 0-0.177 0-0.281 0-15.81-2.855-30.953-8.077-44.942l295.544-169.566c23.265 24.363 56.001 39.509 92.275 39.509 0.020 0 0.039 0 0.059 0 70.689 0 127.997-57.308 127.997-128 0-70.692-57.308-128-128-128-70.692 0-128 57.308-128 128 0 18.965 4.224 36.907 11.627 53.099l-292.288 168.747c-23.653-28.833-59.285-47.084-99.18-47.084-70.692 0-128 57.308-128 128 0 0.188 0 0.376 0.001 0.564-0.001 0.123-0.001 0.304-0.001 0.484 0 70.692 57.308 128 128 128 39.895 0 75.526-18.251 99.001-46.86l289.373 166.752c-5.397 13.568-8.529 29.29-8.533 45.743 0 70.582 57.308 127.889 128 127.889 70.692 0 128-57.308 128-128 0-70.692-57.308-128-128-128z" fill="#3D3D3D" p-id="2811"></path></svg>

          </el-button>
            <div class="content">
                {{ article.data.content }}
            </div>

          <div class="info">
            <span>{{ article.data.author }}</span>
            <span>{{ article.data.tag }}</span>
            <span>ID:{{ article.data.id }}</span>
            <span>{{ article.data.readcount }}阅读数</span>
          </div>
          <svg @click="likeArticle" :class="{'active' : like}" t="1673888330887" class="icon" viewBox="0 0 1024 1024" version="1.1"
               xmlns="http://www.w3.org/2000/svg" p-id="3004" width="32" height="32">
            <path
                d="M190.193225 471.411583c14.446014 0 26.139334-11.718903 26.139334-26.13831 0-14.44499-11.69332-26.164916-26.139334-26.164916-0.271176 0-0.490164 0.149403-0.73678 0.149403l-62.496379 0.146333c-1.425466-0.195451-2.90005-0.295735-4.373611-0.295735-19.677155 0-35.621289 16.141632-35.621289 36.114522L86.622358 888.550075c0 19.949354 15.96767 35.597753 35.670407 35.597753 1.916653 0 3.808746 0.292666 5.649674 0l61.022819 0.022513c0.099261 0 0.148379 0.048095 0.24764 0.048095 0.097214 0 0.146333-0.048095 0.24457-0.048095l0.73678 0 0-0.148379c13.413498-0.540306 24.174586-11.422144 24.174586-24.960485 0-13.55983-10.760065-24.441669-24.174586-24.981974l0-0.393973-50.949392 0 1.450025-402.275993L190.193225 471.409536z"
                fill="#5D5D5D" p-id="3005"></path>
            <path
                d="M926.52241 433.948343c-19.283182-31.445176-47.339168-44.172035-81.289398-45.546336-1.77032-0.246617-3.536546-0.39295-5.380544-0.39295l-205.447139-0.688685c13.462616-39.059598 22.698978-85.58933 22.698978-129.317251 0-28.349675-3.193739-55.962569-9.041934-82.542948l-0.490164 0.049119c-10.638291-46.578852-51.736315-81.31498-100.966553-81.31498-57.264215 0-95.466282 48.15065-95.466282 106.126063 0 3.241834-0.294712 6.387477 0 9.532097-2.996241 108.386546-91.240027 195.548698-196.23636 207.513194l0 54.881958-0.785899 222.227314 0 229.744521 10.709923 0 500.025271 0.222057 8.746198-0.243547c19.35686 0.049119 30.239721-4.817726 47.803749-16.116049 16.682961-10.761088 29.236881-25.50079 37.490869-42.156122 2.260483-3.341095 4.028757-7.075139 5.106298-11.20111l77.018118-344.324116c1.056052-4.053316 1.348718-8.181333 1.056052-12.160971C943.643346 476.446249 938.781618 453.944769 926.52241 433.948343zM893.82573 486.837924l-82.983993 367.783411-0.099261-0.049119c-2.555196 6.141884-6.879688 11.596106-12.872169 15.427364-4.177136 2.727111-8.773827 4.351098-13.414521 4.964058-1.49812-0.195451-3.046383 0-4.620227 0l-477.028511-0.540306-0.171915-407.408897c89.323375-40.266076 154.841577-79.670527 188.596356-173.661202 0.072655 0.024559 0.124843 0.049119 0.195451 0.072655 2.99931-9.137101 6.313799-20.73423 8.697079-33.164331 5.551436-29.185716 5.258771-58.123792 5.258771-58.123792-4.937452-37.98001 25.940812-52.965306 44.364417-52.965306 25.304316 0.860601 50.263777 33.656541 50.263777 52.326762 0 0 5.600555 27.563776 5.649674 57.190537 0.048095 37.366026-4.6673 56.847729-4.6673 56.847729l-0.466628 0c-5.872754 30.879288-16.214287 60.138682-30.464849 86.964654l0.36839 0.342808c-2.358721 4.815679-3.709485 10.220782-3.709485 15.943111 0 19.922748 19.088754 21.742187 38.765909 21.742187l238.761895 0.270153c0 0 14.666024 0.465604 14.690584 0.465604l0 0.100284c12.132318-0.638543 24.221658 5.207605 31.100322 16.409738 5.504364 9.016351 6.437619 19.6045 3.486404 28.988218L893.82573 486.837924z"
                fill="#5D5D5D" p-id="3006"></path>
            <path
                d="M264.827039 924.31872c0.319272 0.024559 0.441045 0.024559 0.295735-0.024559 0.243547-0.048095 0.367367-0.074701-0.295735-0.074701s-0.539282 0.026606-0.271176 0.074701C264.43409 924.343279 264.532327 924.343279 264.827039 924.31872z"
                fill="#5D5D5D" p-id="3007"></path>
          </svg>



          <el-divider />
            <!-- 评论区 -->
            <Comment></Comment>

        </div>
        <div class="right">
            <SideNew></SideNew>
        </div>
    </div>
</template>

<script setup>
import { ref, reactive, onMounted, watch } from 'vue'
import SideNew from '@/components/SideNew.vue'
import Comment from '../../components/comment.vue'
import moment from 'moment'
import { useRoute } from 'vue-router'
import { hot, top } from '@/assets/data/articleData'
import { ElMessage } from 'element-plus'

const route = useRoute()



const { origin } = window.location
const { pathname } = window.location
// 生成链接let copyBtn = document.querySelector('#copy-btn');


function copyText(text) {
  var input = document.createElement('textarea');
  document.body.appendChild(input);
  // 将文本赋值给输入框
  input.value = text;
  // 聚焦并选中
  input.focus();
  input.select();

  // document.queryCommandEnabled()方法返回一个布尔值，表示当前是否可用document.execCommand()的某个命令。
  // 比如copy命令只有存在文本选中时才可用，如果没有选中文本，就不可用。
  if (document.queryCommandEnabled('copy')) {
    // 执行 copy 命令
    var success = document.execCommand('copy');
    // 移除输入框节点
    input.remove();
    console.log('Copy Ok');
  } else {
    console.log('queryCommandEnabled is false');
  }
}

function copyUrl()
{

  var url = window.location.href;

  if (document.queryCommandSupported('copy')) {
    copyText(url);
    alert("成功复制分享链接！")
  } else {
    console.log('当前浏览器不支持 copy命令');
  }

}

//文章信息
const article = reactive({
    data: {
        id: 0,
        title: '',
        author: '',
        tag: '',
        desc: '',
        readcount: 0,
        createTime: '',
        content: ''
    }
})

//获取文章
const getArticle = () => {
    const list = [...hot, ...top]

    list.forEach(item => {
        if (item.id == route.query.id) {
            article.data = item
        }
    })
}

//是否点赞
const like = ref(false)

const likeArticle = () => {
    like.value = !like.value
    if(like.value){
        ElMessage.success('已赞赏，文章将得到推荐')
    }
}

onMounted(() => {

    getArticle()
    //路由携带的id发生变化
    watch(() => route.query.id, () => {

        getArticle()
    })
})

</script>

<style scoped lang='less'>
.articleDetial {
    width: 100%;
    display: flex;
    justify-content: space-between;
    margin-top: 10px;

    &>div {
        background-color: #fff;
        opacity:90%;
    }

    .left {

        width: 69%;
        padding: 20px;

        &>div {
            margin-top: 10px;
            font-size: 16px;
            color: #555;
        }

        .title {
            display: flex;
            align-items: center;
            font-size: 25px;
            color: #333;

            .icon{
                margin-left: 20px;
                cursor: pointer;
            }

            .active{
                path{
                    fill:#ff6d6d;
                }
                
            }
        }

        .info {
            span {
                padding-right: 10px;
            }
        }

        .content {
            color: #222;
            padding: 30px 10px;
            border-top: 1px solid #ccc;
            background-color: #f2f2f2;
            line-height: 30px;
            text-indent: 32px;
        }
    }

    .right {
        width: 29%;
        flex-shrink: 0;
        padding: 20px;
    }
}
</style>