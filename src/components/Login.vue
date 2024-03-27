<template>
  <div class="sub-container">
    
      <h1 >Login</h1>
      <p >Insert you credential to sing in</p>
      <div class="relative mb-4">
        <label for="email">Email</label>
        <input 
          type="email" 
          id="email" 
          name="email"          
          v-model="email"
        >
      </div>
      <div>
        <label for="message" >Password</label>
        <input 
          type="password" 
          id="email" name="email" 
          class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out"
          v-model="password"
        >
      </div>
      <button 
        @click="login()"
      >Sign in</button>
      <p >Laoreet magna curae; maecenas magnis et sed.</p>
    </div>
   
</template>

<script>
import firebase from 'firebase/compat/app'
import db from '../firestore'

export default {
  name: 'Login',
  data () {
    return {
      email: '',
      password: '',
      successMessage: '',
      errorMessage: ''
    }
  },
  methods: {
    login () {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password)
        .then(user => {
          console.log(user)
          alert('authenticated')
          this.$router.push('/dashboard')
        })
        .catch(err => {
          alert('not authenticated!')
          this.errorMessage = err.message
        })
    }
  }
}
</script>


<style >

</style>
