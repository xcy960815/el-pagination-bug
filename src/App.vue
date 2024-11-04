<template>
  <el-button @click="handleSetTotalUndefined">SetTotalUndefined</el-button>
  <el-pagination
    v-model:current-page="currentPage"
    v-model:page-size="pageSize4"
    :page-sizes="[10, 20, 30, 40]"
    layout="total, sizes, prev, pager, next, jumper"
    :total="total"
    @size-change="handleSizeChange"
    @current-change="handleCurrentChange"
  />
</template>

<script lang='ts' setup>
import { ref } from "vue";

const currentPage = ref(1);
const pageSize4 = ref(0);
const total = ref<number | undefined>(400);

const handleSizeChange = (val: number) => {
  console.log(`${val} items per page`);
};

const handleCurrentChange = (val: number) => {
  // 当点击 handleSetTotalUndefined 方法后，不应该触发 handleCurrentChange 方法
  console.log(`current page: ${val}`);
};

const handleSetTotalUndefined = () => {
  total.value = undefined;
};
</script>
<style lang='less' scoped>
</style>