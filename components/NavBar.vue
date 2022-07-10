<template>
    <b-navbar>
        <template #brand>
            <b-navbar-item tag="router-link" :to="{ path: '/' }">
                <img
                    src="http://ww1.prweb.com/prfiles/2020/07/24/17281248/logo-purple-purple.png"
                    alt="Lightweight UI components for Vue.js based on Bulma"
                >
            </b-navbar-item>
        </template>
    

        <template #end>
            <b-navbar-item tag="div">
                <div class="buttons" @click="logout()">
                    <a class="button is-primary">
                        <strong>Logout</strong>
                    </a>
                </div>
            </b-navbar-item>
        </template>
    </b-navbar>

</template>
<script>
import axios from 'axios'

export default {
name: 'NavBar',
  data () {
      return {

      }      
    },
  methods: {
    
      logout(){
    
                axios.post("http://164.92.192.48:8081/logout")
                    .then(response => this.result = response.data.token)
                    .catch(error => { 
                        console.error("There was an error!", error.message) 
                        if(error.message.includes("403")){
                             this.$store.state.auth = false;
                             localStorage.removeItem("token")
                             console.log(this.$store);
                        }
                    })
            }
   }
}   
</script>