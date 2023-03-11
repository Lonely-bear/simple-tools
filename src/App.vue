<script setup lang="ts">
import { reactive } from 'vue';
import CompareList from './components/CompareList.vue';
const formData1 = reactive({
  originalList: "",
  targetList: ""
})

const formData2 = reactive({
  originalList: "王新悦 孙燕 刘王辉 张欣 崔国玉 白秀远 高玮 田林林 石柱明 汪婷 曹仟环 刘毓欣 曾锦龙 夏天赐 李洪龙 范浩坤 刘志刚 张兴乐 李奕君 朱海天 马海波 杨彭杰 符小磊 何成建 罗天祥 苏梦楠 张炀 常飞鸿 王宇辰 唐彪 高金旭 葛子坤 窦梓昕",
  targetList: "张立璟 王鑫 王康 范浩坤 刘志刚 张兴乐 李奕君 朱海天 马海波 杨彭杰 符小磊 何成建 罗天祥 苏梦楠 张炀 常飞鸿 王宇辰 唐彪 高金旭 葛子坤 窦梓昕"
})
</script>

<template>
  <div class="container">
    <h1 class="title">Simple Tools</h1>
    <el-card>
      <template #header>
        <h2>Compare according to the list（列表对比器）</h2>
      </template>
      <el-scrollbar max-height="68vh" class="scrollbar">
        <CompareList :data="formData1" />
        <el-collapse>
          <el-collapse-item title="Here is the example" name="1">
            <CompareList :data="formData2" />
          </el-collapse-item>
        </el-collapse>
      </el-scrollbar>
    </el-card>

    <el-card>
      <template #header>
        <h2>Compare according to the list（列表对比器）</h2>
      </template>
      <el-scrollbar max-height="68vh">
        <CompareList :data="formData1" />
        <el-collapse>
          <el-collapse-item title="Here is the example" name="2">
          </el-collapse-item>
        </el-collapse>
      </el-scrollbar>
    </el-card>
  </div>
</template>

<style scoped>
.container {
  padding: 20px;
  padding-top: 40px;
  display: flex;
  width: 100%;
  box-sizing: border-box;
  height: auto;
  justify-content: space-evenly;
  align-items: flex-start;
  gap: 40px;
  flex-wrap: wrap;
}

.title {
  width: 100%;
  text-align: center;
}

.scrollbar {
  padding-left: 20px;
  padding-right: 20px;
}
</style>
