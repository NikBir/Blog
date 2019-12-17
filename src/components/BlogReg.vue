<template>
    <div class="container">
      <div class="div-inputs">
        <input
            v-model="Name" 
            placeholder="Login" 
            type="text" name="login" 
            id="input-login">
        <input
            v-model="Password" 
            placeholder="Password" 
            type="password" 
            name="password" 
            id="input-password">
      </div>
      <div class="div-btn">
        <button 
            class="btn-signin"
            @click="checkLogin"
        >Sign in</button>
        <span>/</span>
        <button 
            class="btn-signup"
            @click="$emit('checkReg')"
        >Sign up</button>
      </div>
    </div>
</template>

<script>
export default {
    props: ['users'],
    data() {
        return {
            Name: '',
            Password: ''
        }
    },
    mounted() {

    },
    methods: {
        checkLogin() {
            console.log(this.users)
            if (this.Name !== '' && this.Password !== '') {
                for (let i = 0; i < this.users.length; i++) {
                    if (this.users[i].name === this.Name && this.users[i].password === this.Password) {
                        this.$emit('loginTo')
                        this.$emit('nameLogin', this.Name)
                    }
                }
            }
        }
    }
}
</script>

<style lang="scss">
.container {
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 5px;
}
.div-inputs {
  border: 1px solid #aaa;
  border-radius: 5px;
  display: inline-block;
  margin: 0 5px;
  height: 100%;
}
#input-login,
#input-password {
  font-size: 1rem;
  border: none;
  height: 100%;
  padding: 0 15px;
  outline: none;
}
#input-login {
  border-right: 1px solid #aaa;
  border-radius: 5px 0 0 5px;
}
#input-password {
  border-left: 1px solid #aaa;
  border-radius: 0 5px 5px 0;
}
.div-btn {
  display: flex;
  margin: 0 5px;
  height: 100%;
  justify-content: center;
  align-items: center;
}
.div-btn span {
  margin: 10px;
  font-size: 2rem;
  font-weight: 100;
}
.btn-signin,
.btn-signup {
  outline: none;
  display: inline-block;
  height: 100%;
  border-radius: 5px;
  border: 1px solid #444;
  background: #eee;
  padding: 0 20px;
  font-weight: 500;
  font-size: 1.1rem;
  &:hover {
      cursor: pointer;
      background: #444;
      color: #fff;
      box-shadow: 0 0 7px rgba(#444, $alpha: .5);
  }
}
</style>