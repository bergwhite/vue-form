<template>
  <div class="pageSplit">
    <nav aria-label="...">
      <ul class="pagination">
        <li class="disabled">
          <span>
            <span aria-hidden="true">&laquo;</span>
          </span>
        </li>
        <li :class="index === pageCurrent + 1 ? 'active' : ''" v-for="index in pageCount">
          <span>{{index}}<span class="sr-only">(current)</span></span>
        </li>
        <li class="disabled">
          <span>
            <span aria-hidden="true">&raquo;</span>
          </span>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'pageSplit',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  props: ['pageCount', 'pageCurrent']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
