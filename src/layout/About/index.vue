<template>
    <div class="about">
        <div class="main">
            <div class="title">作业报告</div>
            <div class="body">
                <span>艾荣贵 0204329</span>
              <p> 因为最近才看到作业1，老师您的问题，才发现我搞错仓库了，所以重新上传一次，作业一和作业三 包括于大作业要求中，所以我做了重定向。非常抱歉，麻烦老师了。</p>



              <span>网站名称：</span>
              <p>AmlyC Blog</p>
              <br>
              <span>网站主题：</span>
              <p>编程开发，分享实践社区</p>
              <br>
              <span>页面组织结构：</span>
              <p>先是登录与注册页面，主页：主页面中包含三个子页面，最新博文、热门博文和发表页，个人中心页面也包含三个子页面分别是：我的发布、草稿箱、用户设置,管理员习题，文章管理
                笔记系统：菜单栏包括打开、新建、保存、编辑及切换模式，最后一个是本次的大报告。</p>
              <br>




                <span>六、网站内容：</span>
  <br><br>
              <span>主要技术、工具：</span>
              <p>js流行框架vue3、element-ui plus组件库、pinia状态管理插件、vuedraggable拖拽组件、 vue-router路由插件、moment时间格式处理工具、less css预处理语言、json-server工具。</p>
              <br>
              <br>
              <span><h1>1. 主页界面</h1></span><p>
              <img src="../../assets/images/11.jpg" alt="" style="width:90%;height:90%;">
            </p>
              <br><br>
              <p>
                采用在人机交互课程学习到的纯js实现鼠标点击特性
              </p>
              <p>
                <img src="../../assets/images/114.jpg" alt="" style="width:40%;height:40%;">
                <img src="../../assets/images/115.jpg" alt="" style="width:40%;height:40%;">

              </p>
              <br><br>

              <span><h1>2. 笔记系统效果</h1></span>
                <div class="image">
                  <br>
                    <p>可以拖拽，单元格可以拉伸，自动生成序号</p>
                  <br>
                    <img src="../../assets/images/116.jpg" alt="">
                  <br>
                  <br>
                    <p>点击打开对应的笔记文件，可以展开和隐藏该边栏</p>
                  <br>
                    <img src="../../assets/images/17.jpg" alt="">
                  <br>
                  <br><br>

                    <p>点击切换白天与黑夜两种模式</p>
                  <br>
                    <img src="../../assets/images/18.jpg" alt="">
                  <br><br>

                  <p>预览模式</p>
                  <br>
                  <img src="../../assets/images/16.jpg" alt="">
                  <br><br>

                </div>
                <p>1、登录和注册通过表单将数据存储到了json中，通过pinia同步信息，注册后在右侧可以看到相应的账号名(json-server服务器出现问题，现在自动登录为AmlyC)</p>
                <p>2、个人中心，可以进行查看（只可读模式）、编辑和删除</p>
              <br>
              <img src="../../assets/images/110.jpg" alt="" style="width:80%;height:80%;">
              <br>
                <p>3、草稿箱，可以将自己还没写完的博文缓存在这里，可以进行查看、删除、编辑的功能 </p>
                <div class="image">
                    <img src="../../assets/images/caogao.jpg" alt="">
                </div>
                <p>4、用户设置，可以更改自己的昵称、手机号、性别，密码和地址，以及找回密码</p>
                <div class="image">
                    <img src="../../assets/images/112.jpg" alt="">
                  <img src="../../assets/images/113.jpg" alt="">
                </div>



                <p>5、如果需要保存博文，填写好相应的内容后即可保存。</p>
                <div class="image">
                    <img src="../../assets/images/15.jpg" alt="">
                </div>
                <p>6、首页中可以看到热门的博文，还有最近发表的博文，点击博文可以看到相应内容，也可以评论和点赞还有转发分享 </p>
                <div class="image">
                  <img src="../../assets/images/12.jpg" alt="">
                  <img src="../../assets/images/13.jpg" alt="">
                  <img src="../../assets/images/14.jpg" alt="">
                </div>

              <span>开发过程中遇到的问题：</span>
              <p>笔记系统 ：1.实现拖拽功能，点击回车键序号自动按数字增加，本来想着获取单元格的高度来识别单元格的序号，后来用unshift向数组中追加id,当作序号实现的
                点击保存后仅标题保存了，因为要实现单元格且能拖拽，用vuedraggable加循环遍历实现的功能，导致输入的内容不能追加到原有的数组中.<br>2.预览功能 ，不知道如何解析html代码重新覆盖</p>
              <br>
              登录的交互由于网站需要备案 ，之前给的json-server地址无法访问。所以数据库存在问题，本版本直接将登录模式默认为登录。（悲。。。qwq
              <br>


              <br><br>
              <span>亮点：</span>
              <p>1.分享功能2.美观界面，3.找回密码，4.笔记本预览模式</p>
              <br><br>
              <span>最终结果与讨论：</span>
          <p> 尽可能做的美观点了，由于考研的进度，花的时间不是太充足。希望老师手下留情。
              自我评价：良。感觉越做越上头。希望未来能有空，再学点技术，买个服务器域名，把网站备案上去，再优化几下，当自己的博客使用，这就是我未来的展望。
          </p>
            <p>
            最后，谢谢老师的教导！！！
          </p>
              <br><br>
              <br><br>
            </div>
        </div>
    </div>
</template>

<style scoped lang='less'>
*{
  font-family:Arial,Helvetica,sans-serif;font-size:100%;
}
.about{
  font-family:Arial,Helvetica,sans-serif;font-size:100%;

    width: 100%;
    background-color: #fff;
    opacity:90%;
    margin-top:20px;
    font-size:16px;
    padding:20px 0;
    .main{
        width:960px;
        margin:auto;

        .title{
            text-align: center;
            padding:20px 0;
            font-size: 20px;
            margin-bottom: 20px;
        }

        .body{
            span{
                color:#444;
                font-weight: bold;
            }
            p{
                margin-top: 10px;
                text-indent: 32px;
            }
            .image{
                width: 100%;
                padding:20px 0;
                img{
                    width: 100%;
                    height: auto;
                }
            }
        }
    }
}
</style>