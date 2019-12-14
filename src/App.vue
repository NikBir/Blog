<template>
  <div id="app">
    <h1>Blog application</h1>
    <BlogReg v-if="regFlag"/>
    <BlogLoginTo v-else/>
    <hr>
    <BlogList
      v-bind:blogs="blogs"
      @remove-item="removeItem"
    />
    <button class="btn-create-blog"
            v-if="regFlag != true"
            v-on:click='click'>
      <span>Create</span>
      <img src="./icons/createIcon.svg" alt="">
    </button>
    <ModalWindow/>
  </div>
</template>

<script>
import BlogList from '@/components/BlogList'
import BlogReg from '@/components/BlogReg'
import BlogLoginTo from '@/components/BlogLoginTo'
import ModalWindow from '@/components/ModalWindow'
export default {
  name: 'app',
  data() {
    return {
      blogs: [
        {id: 1, title: "Текст блога 1", completed: false},
        {id: 2, title: "Текст блога 2", completed: false},
        {id: 3, title: "Текст блога 3", completed: false}
      ],
      regFlag: false,
      showModal: true
    }
  },
  methods: {
    removeItem(id) {
      this.blogs = this.blogs.filter(t => t.id !== id)
    },
    click: function() {
      this.$emit('show', this.showModal)
    }
  },
  components: { // регистрация новый модулей *.vue
    BlogList,
    BlogReg,
    BlogLoginTo,
    ModalWindow
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
.btn-create-blog {
  outline: none;
  position: absolute;
  right: 30px;
  bottom: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50px;
  border-radius: 25px;
  border: none;
  padding: 12px;
  background-color: rgb(77, 247, 26);
  &:hover {
    cursor: pointer;
    background-color: #fff;
    box-shadow: 0 0 7px rgb(77, 247, 26),
                0 0 0 1px rgb(77, 247, 26) inset;
  }
  span {
    display: inline-block;
    font-size: 1.1rem;
    margin-right: 10px;
  }
  img {
    display: inline-block;
    height: 100%;
  }
}
</style>
