<template>
  <h1 class="title"><el-text>城市-岗位-薪资</el-text></h1>
  <el-table
    :default-sort="{ prop: 'posts', order: 'descending' }"
    class="table"
    :data="data"
    style="width: 80%"
    stripe
  >
    <el-table-column prop="city" label="城市">
      <template #default="scope">
        {{ scope.row.city }}
      </template>
    </el-table-column>
    <el-table-column prop="posts" :sortable="true" label="岗位">
      <template #default="scope">
        {{ scope.row.posts }}
      </template>
    </el-table-column>
    <el-table-column prop="postsTrends" :sortable="true" label="增长">
      <template #default="scope">
        {{ Math.round((scope.row.postsTrends - 1) * 100) }}%
      </template>
    </el-table-column>
    <el-table-column
      prop="mainSalary"
      :sortable="true"
      label="薪资"
      :sort-method="(a, b) => a.mainSalary[1] - b.mainSalary[1]"
    >
      <template #default="scope">
        {{ scope.row.mainSalary[0] }}k ~ {{ scope.row.mainSalary[1] }}k
      </template>
    </el-table-column>
    <el-table-column label="详情">
      <template #default="scope">
        <el-space>
          <el-link
            :href="scope.row.detail.salary"
            target="_blank"
            type="primary"
          >
            薪资
          </el-link>
          <el-link
            :href="scope.row.detail.trends"
            target="_blank"
            type="primary"
          >
            趋势
          </el-link>
        </el-space>
      </template>
    </el-table-column>
  </el-table>
</template>

<script setup>
import data from './assets/data.json';
</script>

<style scoped>
.table {
  margin: 1em auto;
}
.title {
  text-align: center;
  font-size: 1em;
}
.title span {
  font-size: 1.3em;
}
</style>
