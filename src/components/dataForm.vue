<template>
  <div class="dataForm">
    <formList :mockData="parseJSON.length === 0 ? ['加载中...']: mock"></formList>
    <pageSplit :pageCount="pageCount" :pageCurrent="pageCurrent" @changePage="changePage"></pageSplit>
  </div>
</template>

<script>
import formList from './common/formList'
import pageSplit from './common/pageSplit'
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
    formList,
    pageSplit
  },
  methods: {
    // 上一页方法
    prevPage: function() {
      const prev = this.pageCurrent - 1
      prev >= 0 && (this.updatePageList = prev)
    },
    // 下一页方法
    nextPage: function() {
      const next = this.pageCurrent + 1
      next < this.pageCount && (this.updatePageList = next)
    },
    // 下一页方法
    sepcPage: function(index) {
      this.updatePageList = index
    },
    changePage: function(msg) {
      switch (msg.type) {
        case 'prev':
          this.prevPage()
          break;
        case 'next':
          this.nextPage()
          break;
        case 'spec':
          this.sepcPage(msg.index)
          break;
        default:
          break;
      }
    }
  },
  computed: {
    // 动态更新列表
    parseJSON: {
      get: function() {
        return this.mock
      },
      set: function(data) {
        this.mock = data
      }
    },
    // 根据传入的页面索引渲染相应列表
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
        // 更新最近的页面索引
        this.pageCurrent = index
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
    this.updatePageList = 2
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
