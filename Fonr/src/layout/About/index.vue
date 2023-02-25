<template>
    <div class="about">
        <div class="main">
            <div class="title">作业报告</div>
            <div class="body">
                <span>一、主要技术、工具：</span>
                <p>js流行框架vue3、element-ui plus组件库、pinia状态管理插件、vuedraggable拖拽组件、 vue-router路由插件、moment时间格式处理工具、less css预处理语言、json-server工具。</p>
                <br>
                <span>二、开发过程中遇到的问题：</span>
                <p>笔记系统 ：实现拖拽功能，点击回车键序号自动按数字增加，本来想着获取单元格的高度来识别单元格的序号，后来用unshift向数组中追加id,当作序号实现的
                    点击保存后仅标题保存了，因为要实现单元格且能拖拽，用vuedraggable加循环遍历实现的功能，导致输入的内容不能追加到原有的数组中</p>
                <br>
                <span>三、网站名称：</span>
                <p>编程Blog</p>
                <br>
                <span>四、网站主题：</span>
                <p>编程开发，分享实践社区</p>
                <br>
                <span>五、页面组织结构：</span>
                <p>先是登录与注册页面，主页：主页面中包含三个子页面，最新博文、热门博文和发表页，个人中心页面也包含三个子页面分别是：我的发布、草稿箱、用户设置
                    笔记系统：菜单栏包括打开、新建、保存、编辑及切换模式，最后一个是本次的报告。</p>
                <br>
                <span>六、网站内容：</span>
                <span>笔记系统效果</span>
                <div class="image">
                    <p>可以拖拽，单元格可以拉伸，自动生成序号</p>
                    <img src="../../assets/images/微信图片_202302252006153.png" alt="">
                    <p>点击打开对应的笔记文件，可以展开和隐藏该边栏</p>
                    <img src="../../assets/images/微信图片_202302252006154.png" alt="">
                    <p>点击切换白天与黑夜两种模式</p>
                    <img src="../../assets/images/微信图片_202302252006155.png" alt="">

                </div>
                <p>1、登录和注册通过表单将数据存储到了json中，通过pinia同步信息，注册后在右侧可以看到相应的账号名</p>
                <p>2、个人中心，可以进行查看（只可读模式）、编辑和删除</p>
                <div class="image">
                    <img src="../../assets/images/微信图片_20230225200615.png" alt="">
                </div>
                <p>3、草稿箱，可以将自己还没写完的博文缓存在这里，可以进行查看、删除、编辑的功能 </p>
                <div class="image">
                    <img src="../../assets/images/微信图片_202302252006151.png" alt="">
                </div>
                <p>4、用户设置，可以更改自己的昵称、手机号、性别和密码。</p>
                <div class="image">
                    <img src="../../assets/images/微信图片_20230225203035.png" alt="">
                </div>
                <p>5、如果需要保存博文，填写好相应的内容后即可保存。</p>
                <div class="image">
                    <img src="../../assets/images/微信图片_20230225202337.png" alt="">
                </div>
                <p>6、首页中可以看到热门的博文，还有最近发表的博文，点击博文可以看到相应内容，也可以评论和点赞 </p>
                <div class="image">
                    <img src="../../assets/images/微信图片_20230225202633.png" alt="">
                </div>
                <div class="image">
                    <img src="../../assets/images/微信图片_202302252026331.png" alt="">
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped lang='less'>
.about{
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