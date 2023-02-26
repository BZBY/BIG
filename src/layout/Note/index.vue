<template>
  <el-menu
    :default-active="activeIndex"
    class="el-menu-demo"
    mode="horizontal"
    @select="handleSelect"
    :style="{ 'background-color': Day.day ? '#000' : '#fff' }"
  >
    <el-menu-item index="1" @click="drawer = true"
      >打开<el-icon><FolderOpened /></el-icon
    ></el-menu-item>
    <el-menu-item index="3"
      >新建<el-icon><DocumentAdd /></el-icon
    ></el-menu-item>
    <el-menu-item index="4" @click="save"
      >保存<el-icon><Folder /></el-icon
    ></el-menu-item>
    <el-menu-item index="5"
      >编辑<el-icon><Edit /></el-icon
    ></el-menu-item>

    <el-sub-menu index="2">
      <template #title
        >主题模式<el-icon><Sunrise /></el-icon
      ></template>
      <el-menu-item index="2-1" @click="changeBlock">白天</el-menu-item>
      <el-menu-item index="2-2" @click="changeDay">夜间</el-menu-item>
    </el-sub-menu>
  </el-menu>
  <div class="h-6" />
  <el-menu
    :default-active="activeIndex2"
    class="el-menu-demo"
    mode="horizontal"
    background-color="#545c64"
    text-color="#fff"
    active-text-color="#ffd04b"
    @select="handleSelect"
  >
  </el-menu>

  <el-drawer
    v-model="drawer"
    title="编程笔记"
    :direction="direction"
    size="20%"
  >
    <div v-for="item in noteData" :key="item.id">
      <span ref="noteText" class="note" @click="check(item)">{{
        item.name
      }}</span>
    </div>
  </el-drawer>
  <div class="content" >
    <div class="open" v-if="mode.type == 'open'">
      {{ current.note.content }}
    </div>
    <div class="built" v-if="mode.type == 'newBuilt'">
            <el-input
              v-model="list.name"
              placeholder="请输入标题(最多输入15字)"
               size="large"
               clearable
               maxlength=15
               class="inputSize"
            />

      <draggable
        :list="list"
        ghost-class="ghost"
        :force-fallback="true"
        chosen-class="chosenClass"
        animation="300"
        @start="onStart"
        @end="onEnd"
      >
        <template #item="{ element }">
          <div class="cells">
            <div class="order">{{ element.id }}</div>
            <el-input
              v-model="element.content"
              placeholder="请按回车键确认添加,可拖拽排序"
              @keyup.enter="addAttrinTypeList(element.id)"
              type="textarea"
            />
            <div class="Fin"></div>
          </div>
        </template>
      </draggable>
    </div>
    <div class="save" v-if="mode.type == 'save'">
      <div  class="inputSize">{{list.name}}</div>
      <draggable
        :list="list"
        ghost-class="ghost"
        :force-fallback="true"
        chosen-class="chosenClass"
        animation="300"
        @start="onStart"
        @end="onEnd"
      >
        <template #item="{ element }">
          <div class="cells">
            <div class="order">{{ element.id }}</div>
            <div class="con">{{ element.content }}</div>
          </div>
        </template>
      </draggable>
    </div>
    <div class="edit" v-if="mode.type == 'edit'">
         <el-input
              v-model="list.name"
              placeholder="请输入标题(最多输入15字)"
               size="small"
               clearable
               maxlength=15
               class="inputSize"
            />
      <draggable
        :list="list"
        ghost-class="ghost"
        :force-fallback="true"
        chosen-class="chosenClass"
        animation="300"
        @start="onStart"
        @end="onEnd"
      >
        <template #item="{ element }">
  
          <div class="cells">
            <div class="order">{{ element.id }}</div>
            <el-input
              v-model="element.content"
              placeholder="请按回车键确认添加,可拖拽排序"
              @keyup.enter="addAttrinTypeList(element.id)"
            >
              <template #append
                ><el-icon @click="remove(element.id)"><Close /></el-icon
              ></template>
            </el-input>
          </div>
        </template>
      </draggable>
    </div>
  </div>
</template>



<script lang="ts" setup>
import noteData from "../../assets/data/noteData";
import draggable from "vuedraggable";
import { useStore } from "@/stores/useStore";
import { Close } from "@element-plus/icons-vue";
import { reactive, ref } from "vue";
import { ElMessageBox, ElMessage } from "element-plus";
const Day = useStore();

const activeIndex = ref("5");
const activeIndex2 = ref("5");
const handleSelect = (key: string, keyPath: string[]) => {
  if (key == 1) {
    mode.type = "open";
  }
  if (key == 3) {
    mode.type = "newBuilt";
  }
  if (key == 4) {
    mode.type = "save";
  }
  if (key == 5) {
    mode.type = "edit";
  }
  if (key == "") {
    mode.type = "open";
  }
};

const mode = reactive({
  type: "open",
  type: "newBuilt",
  type: "save",
  type: "edit",
});
let list = reactive([{ id: 1, content: '' ,name:''}]);


const addAttrinTypeList = (id) => {
  list.unshift({
    content:'',
    name:'',
    id: id + 1,
  });
};
const drawer = ref(false);
const direction = ref("ltr");
const radio1 = ref("Option 1");

//当前笔记
const current = reactive({
  note: {},
});

//查看
const check = (item) => {
  // console.log(item);
  current.note = item;
};
//白天
const changeDay = () => {
  Day.changeDay();
};
//黑夜
const changeBlock = () => {
  Day.changeBlock();
};
//保存
const save = () => {
  noteData.unshift({
    content:list.content,
    name:list.name,
    id:list.id,
  });
  ElMessage.success("保存成功");
};
//splice删除方法
const remove = (id) => {
  list.forEach((item, index, arr) => {
    if (item.id == id) {
      arr.splice(index, 1);
    }
  });
};
</script>
<style scoped lang='less'>
/* body{
  background-color: #000;
} */

.inputSize{
  margin-left:40%;
  width: 20%;
  text-align: center;
}
.note {
  padding: 8px 0;
  display: block;
}
.content {
  margin: 10px 50px;
  border: 2px solid #4362d7;
  padding: 8px 15px;
  height: 30vw;
  overflow: auto;
}
.cells {
  display: flex;
  align-items: center;
}
.order {
  color: #ffffff;

  padding: 4px 6px;
  border: #fff 1px solid;
}
.con {
  padding: 4px 6px;
  margin: 1px 0;
  width: 100%;
  height: 31px;
  border: #e7e7e7 1px solid;
  background-color: #fff;
}
:deep .el-textarea__inner {
  padding: 0;
  padding-top: 8px;
  line-height: 1;
  min-height: 20px;
}
</style>
