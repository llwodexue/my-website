<script setup>
import { ElTable, ElTableColumn } from 'element-plus'

const tableData = [
  {
    url: 'http://182.92.10.187/',
    desc: 'http://llmysnow.top/'
  },
  {
    url: 'http://182.92.10.187:8080/',
    desc: 'Vue2.7项目地址'
  },
  {
    url: 'http://182.92.10.187:8081/',
    desc: 'Jenkins地址（内存占用太高，暂停访问）'
  },
  {
    url: 'http://182.92.10.187:8082/',
    desc: 'Nexus3私库地址（内存占用太高，暂停访问）'
  },
  {
    url: 'http://182.92.10.187:8083/',
    desc: 'Yapi地址'
  }
]

const mdData = [
  {
    url: 'http://182.92.10.187:9090/',
    desc: 'Vue3离线文档'
  },
  {
    url: 'http://182.92.10.187:9091/',
    desc: 'ElementPlus离线文档'
  },
  {
    url: 'http://182.92.10.187:9092/',
    desc: 'ElementUI离线文档'
  },
  {
    url: 'http://182.92.10.187:9093/',
    desc: '云服务器部署文档'
  }
]
</script>

<template>
  <div class="app-container">
    <div class="table-search card">
      <div>项目链接</div>
    </div>
    <div class="table-container card">
      <el-table :data="tableData" stripe fit style="width: 100%">
        <el-table-column prop="url" label="项目地址" min-width="220">
          <template #default="{ row }">
            <a :href="row.url" target="_blank" style="color: #0633ff">
              {{ row.url }}
            </a>
          </template>
        </el-table-column>
        <el-table-column prop="desc" label="项目描述" min-width="180" />
      </el-table>
    </div>

    <div class="table-search card">
      <div>文档链接</div>
    </div>
    <div class="table-container card">
      <el-table :data="mdData" stripe fit style="width: 100%">
        <el-table-column prop="url" label="项目地址" min-width="220">
          <template #default="{ row }">
            <a :href="row.url" target="_blank" style="color: #0633ff">
              {{ row.url }}
            </a>
          </template>
        </el-table-column>
        <el-table-column prop="desc" label="项目描述" min-width="180" />
      </el-table>
    </div>
  </div>
</template>

<style scoped>
.app-container {
  width: 100%;
  margin: auto;
}
.card {
  padding: 15px 10px 0px 10px;
  box-sizing: border-box;
  overflow-x: hidden;
  background-color: #fff;
  border: 1px solid #e4e7ed;
  border-radius: 4px;
  box-shadow: 0 0 12px rgb(0 0 0 / 5%);
}
.table-container {
  margin-bottom: 10px;
}
.table-search {
  margin-bottom: 2px;
}
.table-search:before {
  content: '';
  float: left;
  width: 4px;
  height: 30px;
  background: #0633ff;
  margin-right: 6px;
}
</style>

<style>
.el-table--striped .el-table__body tr.el-table__row--striped td {
  background: #eff2ff !important;
}
</style>
