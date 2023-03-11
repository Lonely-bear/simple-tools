<script setup lang="ts">
import { reactive, computed } from 'vue';
type formDataType = { originalList: string; targetList: string; }
const { data } = defineProps<{
    data: formDataType
}>()

const formData = reactive({...data});

const overlap = computed(() => {
    if (formData.originalList && formData.targetList) {
        let finalArray1 = [...new Set(formData.originalList.split(' '))].filter(item => [...new Set(formData.targetList.split(' '))].includes(item) && item !== '');
        let finalArray2 = [...new Set(formData.targetList.split(' '))].filter(item => [...new Set(formData.originalList.split(' '))].includes(item) && item !== '');
        let finalArray = [...new Set([...finalArray1, ...finalArray2])];
        return finalArray.length === 0 ? 'The two lists don\'t have same item' : finalArray.join(" ");
    } else {
        return 'Please type the lists';
    }
})

const O_Diff_T = computed(() => {
    if (formData.originalList && formData.targetList) {
        let finalArray = [...new Set(formData.originalList.split(' '))].filter(item => ![...new Set(formData.targetList.split(' '))].includes(item) && item !== '');
        return finalArray.length === 0 ? 'Original list not diffrent with Target list' : finalArray.join(" ");
    } else {
        return 'Please type the lists';
    }
})

const T_Diff_O = computed(() => {
    if (formData.originalList && formData.targetList) {
        let finalArray = [...new Set(formData.targetList.split(' '))].filter(item => ![...new Set(formData.originalList.split(' '))].includes(item) && item !== '');
        return finalArray.length === 0 ? 'Target list not diffrent with Original list' : finalArray.join(" ");
    } else {
        return 'Please type the lists';
    }
})

const O_Diff_T__AND__T_Diff_O = computed(() => {
    if (formData.originalList && formData.targetList) {
        let finalArray1 = [...new Set(formData.originalList.split(' '))].filter(item => ![...new Set(formData.targetList.split(' '))].includes(item) && item !== '');
        let finalArray2 = [...new Set(formData.targetList.split(' '))].filter(item => ![...new Set(formData.originalList.split(' '))].includes(item) && item !== '');
        let finalArray = [...new Set([...finalArray1, ...finalArray2])];
        return finalArray.length === 0 ? 'The two lists are same' : finalArray.join(" ");
    } else {
        return 'Please type the lists';
    }
})

</script>

<template>
    <el-form :model="formData" label-width="200px" label-position="top">
        <el-form-item label="Original list">
            <el-input type="textarea" v-model="formData.originalList" placeholder="Please input the original list"></el-input>
        </el-form-item>
        <el-form-item label="Target list">
            <el-input type="textarea" v-model="formData.targetList" placeholder="Please input the target list"></el-input>
        </el-form-item>
        <el-form-item label="Overlap">
            <el-input type="textarea" readonly v-model="overlap" placeholder="Do not input anything"></el-input>
        </el-form-item>
        <el-form-item label="O_Diff_T">
            <el-input type="textarea" readonly v-model="O_Diff_T" placeholder="Do not input anything"></el-input>
        </el-form-item>
        <el-form-item label="T_Diff_O">
            <el-input type="textarea" readonly v-model="T_Diff_O" placeholder="Do not input anything"></el-input>
        </el-form-item>
        <el-form-item label="O_Diff_T__AND__T_Diff_O">
            <el-input type="textarea" readonly v-model="O_Diff_T__AND__T_Diff_O" placeholder="Do not input anything"></el-input>
        </el-form-item>
    </el-form>
</template>