<template>
  <div id="app">
    <h1>Blog application</h1>
    <BlogReg v-if="regFlag"/>
    <BlogLoginTo v-else/>
    <AddBlogItem/>
    <hr>
    <BlogList
      v-bind:blogs="blogs"
      @remove-item="removeItem"
    />
  </div>
</template>

<script>
import BlogList from '@/components/BlogList'
import BlogReg from '@/components/BlogReg'
import BlogLoginTo from '@/components/BlogLoginTo'
import AddBlogItem from '@/components/AddBlogItem'
export default {
  name: 'app',
  data() {
    return {
      blogs: [
        {id: 1, title: "Текст блога 1", completed: false},
        {id: 2, title: "Текст блога 2", completed: false},
        {id: 3, title: "Текст блога 3", completed: false}
      ],
      regFlag: true
    }
  },
  methods: {
    removeItem(id) {
      this.blogs = this.blogs.filter(t => t.id !== id)
    }
  },
  components: { // регистрация новый модулей *.vue
    BlogList,
    BlogReg,
    BlogLoginTo,
    AddBlogItem
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
hr {
  margin: 30px 0;
}
</style>
