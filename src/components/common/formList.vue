<template>
  <div class="formList">
    <table class="table table-bordered table-hover">
      <thead>
          <tr>
          <td>书名</td>
          <td>作者</td>
          <td>译者</td>
          <td>出版社</td>
          <td>出版年份</td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="dataList in mockData">
          <td>{{dataList.bookTitle}}</td>
          <td>{{dataList.bookAuthor}}</td>
          <td>{{dataList.bookTrans}}</td>
          <td>{{dataList.bookPublish}}</td>
          <td>{{dataList.bookYear}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'formList',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  props: ['mockData']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
