<template>
  <!-- 发布文章 -->
  <div class="myCreate">
    <div class="articleArea">
      <div class="title">
        <el-form-item label="标题">
          <el-input
            v-model="article.title"
            placeholder="请输入文章标题（3-20）字"
          ></el-input>
        </el-form-item>
      </div>
      <el-divider />
      <div class="author">
        <div>
          <el-form-item label="分类专栏">
            <el-input
              v-model="article.author"
              placeholder="请输入类型"
            ></el-input>
          </el-form-item>
        </div>
        <div>
          <el-form-item label="文章标签" >
            <el-input v-model="article.tag" placeholder="请输入标签"></el-input>
          </el-form-item>
        </div>
      </div>
      <div class="type">
        <el-form-item label="内容等级">
          <el-radio-group v-model="article.grade">
            <el-radio label="初级" />
            <el-radio label="中级" />
            <el-radio label="高级" />
          </el-radio-group>
        </el-form-item>
      </div>
      <div class="content">
        <el-form-item label="正文">
          <el-input
            :autosize="{ minRows: 20, maxRows: 35 }"
            type="textarea"
            v-model="article.content"
          ></el-input>
        </el-form-item>
      </div>

      <div class="btn">
        <el-button type="primary" @click="publish">发布</el-button>
        <el-button @click="save">保存</el-button>
      </div>
    <!-- <Publish></Publish> -->

    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from "vue";
import { ElMessage } from "element-plus";
import { useUser } from "@/stores/useLogin";

// import Publish  from "../Center/index.vue"
import { useRouter } from "vue-router";

const User = useUser();
const router = useRouter();

const article = reactive({
  data: {
    id: 99,
    title: "",
    author: "",
    tag: "",
    grade: "",
    desc: "",
    readcount: 0,
    createTime: new Date(),
    content: "",
  },
});

const publish = () => {
  if (!User.isLogin) {
    ElMessage.error("未登录，请登录后再发布");
    router.push({ path: "/login" });
  } else {
    if (
      !article.data.title == "" ||
      !article.data.tag == "" ||
      !article.data.content == ""
    ) {
      ElMessage.error("请正确填写标题、标签、正文");
    } else {
      ElMessage.success("发布成功");
    }
  }
};

const save = () => {
  if (!User.isLogin) {
    ElMessage.error("未登录，请登录后再保存");
    router.push({ path: "/login" });
  } else {
    if (
      article.data.title == "" ||
      !article.data.tag == "" ||
      !article.data.content == ""
    ) {
      ElMessage.error("请正确填写标题、标签、正文");
    } else {
      ElMessage.success("保存成功");
    }
  }
};
</script>

<style scoped lang='less'>
.myCreate {
  margin-top: 20px;
  padding: 20px;
  background-color: #fff;
  opacity:90%;
  color: #100f0f;
  font-weight:bold;
  .articleArea {
    font-weight:bold;
    padding: 20px;
    width: 70%;
    margin: 0 auto;
    border: 1px solid #0e7bef;
    background-color: #808bb9;
    border-radius: 13px;
    & > div {
      margin-bottom: 10px;
    }

    .title {
      width: 100%;
    }

    .author {
      width: 100%;
      margin-top: 20px;
      display: flex;

      & > div {
        width: 30%;
        margin-right: 20px;
      }
    }

    .btn {
      width: 100%;
      text-align: end;
    }
  }
}
</style>