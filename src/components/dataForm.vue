<template>
  <div class="dataForm">
    <formList :mockData="parseJSON.length === 0 ? ['加载中...']: mock"></formList>
  </div>
</template>

<script>
import formList from './common/formList'
import mock from '../assets/mock.json'
export default {
  name: 'dataForm',
  data () {
    return {
      mock: [],
      mockList: [],
      listPerPage: 5,
      listAll: 1,
      pageCount: 1,
      pageCurrent: 0,
      pageNext: '',
      pagePrev: '',

    }
  },
  components: {
    formList
  },
  computed: {
    parseJSON: {
      get: function() {
        return this.mock
      },
      set: function(data) {
        this.mock = data
      }
    },
    updatePageList: {
      get: function() {
        return this.mock
      },
      set: function(index) {
        // 每页列表数量
        const listPerPage = this.listPerPage
        // 模拟数据
        const mockMess = this.mockList
        // 当前页面开始的索引
        const pageFromIndex = index * listPerPage
        // 统计列表的数量
        this.listAll = mockMess.length
        // 统计页面的数量
        this.pageCount = Math.ceil(this.listAll / listPerPage)
        // 解析当前页面的数据
        this.parseJSON = mockMess.slice(pageFromIndex, listPerPage + pageFromIndex)
      }
    }
  },
  mounted() {
    this.mockList = mock.resMess
    this.updatePageList = 1
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
