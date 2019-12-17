<template>
  <div id="app">
    <h1>Blog application</h1>
    <BlogReg 
      v-if="regFlag"
      v-bind:users="DataUser"
      @loginTo="loginTo"
      @nameLogin="nameLogin"
      @checkReg='checkReg'
    />
    <BlogLoginTo 
      v-else
      v-bind:nameLogin="Name"
      @checkExit="checkExit"/>
    <hr>
    <BlogList
      v-if="blogs.length !== 0"
      v-bind:blogs="blogs"
      v-bind:checkLogin="this.regFlag"
      @remove-item="removeItem"
    />
    <span
      v-else-if="blogs.length === 0"
    >There are no posts yes</span>
    <button class="btn-create-blog"
            v-if="regFlag != true"
            v-on:click='click'>
      <span>Create</span>
      <img src="./icons/createIcon.svg" alt="">
    </button>
    <ModalWindow
      @add-blog='addBlog'
    />
    <ModalReg
      v-if="signUp"
      @dereg="dereg"
      @okReg="okReg"
    />
  </div>
</template>

<script>
import DataBlog from '@/data/data-blog.json'
import DataUser from '@/data/data-user.json'
import BlogList from '@/components/BlogList'
import BlogReg from '@/components/BlogReg'
import BlogLoginTo from '@/components/BlogLoginTo'
import ModalWindow from '@/components/ModalWindow'
import ModalReg from '@/components/ModalReg'
export default {
  name: 'app',
  data() {
    return {
      blogs: [],
      regFlag: true,
      signUp: false,
      showModal: true,
      DataBlog,
      DataUser
    }
  },
  created() {
    this.blogs = this.DataBlog
  },
  methods: {
    removeItem(id) {
      this.blogs = this.blogs.filter(t => t.id !== id)
    },
    click: function() {
      this.$emit('show', this.showModal)
    },
    addBlog(blog) {
      this.blogs.push(blog)
    },
    login() {
      this.blogs.length !== 0
    },
    loginTo() {
      this.regFlag = false
    },
    nameLogin(data) {
      this.Name = data
    },
    checkExit(data) {
      this.regFlag = data
    },
    checkReg() {
      this.signUp = true
    },
    dereg() {
      this.signUp = false
    },
    okReg(login, pass) {
      this.signUp = false
      this.Name = login
      let obj = {
        table: []
      }
      obj.table = this.DataUser
      obj.table.push({name: login, password: pass})
      this.DataUser = obj.table
      this.regFlag = false
    }
  },
  components: { // регистрация новый модулей *.vue
    BlogList,
    BlogReg,
    BlogLoginTo,
    ModalWindow,
    ModalReg
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
  position: fixed;
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
    box-shadow: 0 0 10px rgb(77, 247, 26),
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
