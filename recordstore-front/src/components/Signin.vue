<template>
  <div class="max-w-sm m-auto my-8">
    <div class="border p-10 border-gray-300 shadow rounded">
      <h3 class="text-2xl mb-6 text-grey-darkest">
        Sign in
      </h3>
      <form @submit.prevent="signin">
        <div class="text-red" v-if="error">{{ error }}</div>

        <div class="mb-6">
          <label for="email" class="label">E-mail Address</label>
          <input type="email" v-model="email" class="input" id="email" placeholder="yout@email" />
        </div>

        <div class="mb-6">
          <label for="password" class="label">Password</label>
          <input type="password" v-model="password" class="input" id="password" />
        </div>

        <button class="fonts-sans font-bold px-4 rounded cursor-pointer no-underline bg-green-600 hover:bg-green-900 block w-full py-4 text-white items-center justify-center">
          Sign In
        </button>

        <div class="my-4">
          <router-link to="/signup" class="link-grey">Sign Up</router-link>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Signin',
  data () {
    return {
      email: '',
      password: '',
      error: ''
    }
  },
  created () {
    this.checkSignIn()
  },
  updated () {
    this.checkSignIn()
  },
  methods: {
    signin () {
      this.$http.plain.post('/signin', { email: this.email, password: this.password })
        .then(response => { this.signinSuccessful(response) })
        .catch(error => this.signinFailed(error))
    },
    signinSuccessful (response) {
      if (!response.data.csrf) {
        this.signinFailed(response)
        return
      }

      localStorage.csrf = response.data.csrf
      localStorage.signedIn = true
      this.error = ''
      this.$router.replace('/records')
    },
    signinFailed (error) {
      this.error = (error.response && error.response.data && error.response.data.error) || ''
      delete localStorage.csrf
      delete localStorage.signin
    },
    checkSignIn () {
      if (localStorage.signin) {
        this.$router.replace('/records')
      }
    }
  }
}
</script>
