<template>
  <div id="app">
    <h1>Vue-Paginate v3.0</h1>
    <!-- //per 每页显示几条 -->
    <paginate name="items" :per="2" :list="items" ref="paginator" class="paginate-list">
      <li v-for="item in paginated('items')">
        {{ item }}
      </li>
    </paginate>
    <paginate-links for="items"
      :show-step-links="true"
    ></paginate-links>
    <paginate-links for="items"
      :show-step-links="true"
      :limit="1"
      :step-links="{
        next: 'N',
        prev: 'P'
      }"
    ></paginate-links>
    <paginate-links for="items" :simple="{
      next: 'Next »',
      prev: '« Back'
    }"></paginate-links>
    <span v-if="$refs.paginator">
      Viewing {{$refs.paginator.pageItemsCount}} results
    </span>
  </div>
</template>

<script>
export default {
  data () {
    return {
      items: ['JavaScript', 'PHP', 'HTML', 'CSS', 'Ruby', 'Python', 'Erlang'],
      paginate: ['items']
    }
  }
}
</script>

<style lang="sass">
#app
  font-family: 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  font-size: 20px
  text-align: center
  color: #2c3e50
  margin-top: 60px
h1, h2
  font-weight: normal
ul
  list-style-type: none
  padding: 0
li
  display: inline-block
  margin: 0 10px
.paginate-list
  width: 159px
  margin: 0 auto
  text-align: left
  li
    display: block
    &:before
      content: '⚬ '
      font-weight: bold
      color: slategray
    
.paginate-links.items
  user-select: none
  a
    cursor: pointer
  
  li.active a
    font-weight: bold
  
  li.next:before
    content: ' | '
    margin-right: 13px
    color: #ddd
  
  li.disabled a
    color: #ccc
    cursor: no-drop
  
a
  color: #42b983
</style>

