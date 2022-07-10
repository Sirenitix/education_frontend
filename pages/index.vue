<template>
  <LoginPage v-if="$store.getters.auth === false"></LoginPage>
  <Home v-else-if="$store.getters.auth === true"></Home>
</template>

<script>
import LoginPage from '~/components/LoginPage'
import Home from '~/components/Home.vue'
import Vuex from 'vuex'
import Vue from 'vue'


Vue.use(Vuex)
const store = new Vuex.Store({
  state: {
    auth: localStorage.token ? true : false 
  },
  mutations: {
    authReverse () {
      state.auth = !state.auth
    }
  },
  getters: {
   auth: state => {
     return state.auth
   }
  }
})



export default {
  store,
  name: 'IndexPage',
  components: {
    LoginPage,
    Home
  },
   data () {
    return{
      
    }
      
      }
  
}
</script>
