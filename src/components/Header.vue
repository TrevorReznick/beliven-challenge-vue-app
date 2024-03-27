<template>
  <header >
    <div >
      <router-link to="/" >
        <span >Firebase Auth</span>
      </router-link>
    <nav >
      <router-link to="/" class="mr-5 hover:text-gray-900">Home</router-link>
      <router-link to="/login" >Login</router-link>
      <router-link to="/register" >Register</router-link>      
      <a a href="#" @click.prevent.stop="logout" class="mr-5 hover:text-gray-900">Logout</a>
    </nav>
    
  </div>
</header>
 
</template>

<script>

import firebase from 'firebase/compat/app'

export default {
  name: 'Header',
  methods: {
    logout () {
      firebase.auth().signOut()
        .then(() => {
          this.$router.replace('login')
        })
    }
  }
}
</script>
