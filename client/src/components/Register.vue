<template>
  <div>
    <h1>Register</h1>
    <input v-model="email" type="text" name="email" placeholder="email" />
    <br />
    <input v-model="password" type="password" name="password" placeholder="password" />
    <br/>
    <button
    @click="register">Register</button>
  </div>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    async register () {
      const response = await AuthenticationService.register({
        email: this.email,
        password: this.password
      })
      console.log(response.data)
    }
  },
  watch: {
    email (value) {
      console.log('email has change: ', value)
    }
  },
  mounted () {
    setTimeout(() => {
      this.email = 'hello world'
    }, 1000)
  }
}
</script>

<style scoped>

</style>
