<template>
  <div class="app-container">
    <el-table :data="list" border fit highlight-current-row>
      <el-table-column align="center" label="序号" width="95">
        <template slot-scope="scope">
          {{ scope.$index }}
        </template>
      </el-table-column>
      <el-table-column label="商品id">
        <template slot-scope="scope">
          {{ scope.row.id }}
        </template>
      </el-table-column>
      <el-table-column label="商品类目id">
        <template slot-scope="scope">
          {{ scope.row.categoryId }}
        </template>
      </el-table-column>
      <el-table-column label="商品名称">
        <template slot-scope="scope">
          {{ scope.row.name }}
        </template>
      </el-table-column>
      <el-table-column label="商品副标题">
        <template slot-scope="scope">
          {{ scope.row.subtitle }}
        </template>
      </el-table-column>
      <el-table-column label="商品图片">
        <template slot-scope="scope">
          {{ scope.row.mainImage }}
        </template>
      </el-table-column>
      <el-table-column label="商品价格">
        <template slot-scope="scope">
          {{ scope.row.price }}
        </template>
      </el-table-column>
      <el-table-column label="商品在售状态">
        <template slot-scope="scope">
          {{ scope.row.status }}
        </template>
      </el-table-column>
      <!-- <el-table-column label="Title">
        <template slot-scope="scope">
          {{ scope.row.title }}
        </template>
      </el-table-column>
      <el-table-column label="Author" width="110" align="center">
        <template slot-scope="scope">
          <span>{{ scope.row.author }}</span>
        </template>
      </el-table-column>
      <el-table-column label="Pageviews" width="110" align="center">
        <template slot-scope="scope">
          {{ scope.row.pageviews }}
        </template>
      </el-table-column>
      <el-table-column class-name="status-col" label="Status" width="110" align="center">
        <template slot-scope="scope">
          <el-tag :type="scope.row.status | statusFilter">{{ scope.row.status }}</el-tag>
        </template>
      </el-table-column>
      <el-table-column align="center" prop="created_at" label="Display_time" width="200">
        <template slot-scope="scope">
          <i class="el-icon-time" />
          <span>{{ scope.row.display_time }}</span>
        </template>
      </el-table-column> -->
    </el-table>
  </div>
</template>

<script>
  import request from '../../utils/request';
  export default {
    data() {
      return {
        list: []
      }
    },
    created() {
      this.fetchData()
    },
    methods: {
      fetchData() {
        request({
          url: '/products',
          methods: 'get'
        }).then((res) => {
          this.list = res.list
        })
      }
    }
  }
</script>