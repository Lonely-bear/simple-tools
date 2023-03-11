<script setup lang="ts">
import { reactive } from 'vue';
import CompareList from './components/CompareList.vue';
const formData1 = reactive({
  originalList: "",
  targetList: ""
})

const formData2 = reactive({
  originalList: "Helen David Bob Alice Killy",
  targetList: "David Cally"
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
