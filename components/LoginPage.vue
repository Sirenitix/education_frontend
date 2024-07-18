<template>
<div style="display: flex;
                  justify-content: center; 
                  align-items: center;">

 <section>

        <b-field label="Username"
            :type="{ 'is-danger': hasError }"
            :message="{ 'Username is not available': hasError }">
            <b-input v-model="username" placeholder="Email" maxlength="30"></b-input>
        </b-field>

        <b-field label="Password"
            :type="{ 'is-danger': hasError }"
            :message="[
                { 'Password is too short': hasError },
                { 'Password must have at least 8 characters': hasError }
            ]">
            <b-input v-model="password" placeholder="Password" type="password" maxlength="30"></b-input>
        </b-field>
                    <b-button type="is-primary" @click="login()" >Login</b-button>

    </section>
  </div>
</template>

<script>
import axios from 'axios'



export default {



  name: 'LoginPage',
  data () {
      return {
        username: '',
        password: '',
        hasError: false,
        result: ''


      }
    
},

   methods: {
    
      login(){
        const credentials = {
                    username: this.username,
                    password: this.password
        };
                // axios.post("http://164.92.192.48:8081/authenticate", credentials)
                //     .then(response => this.result = response.data.token)
                //     .catch(error => { console.error("There was an error!", error.message) })
       const requestOptions = {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(credentials)
  };
      fetch("http://164.92.192.48:8081/authenticate", requestOptions)
            .then(response => response.json())
            .then(data => (this.result = data.token));
        console.log(this.result)
        if(this.result) {
            this.$store.state.auth = true
            localStorage.setItem("token", this.result)
        }
      
      fetch("http://164.92.192.48:8081/authenticate", requestOptions)
            .then(response => response.json())
            .then(data => 
            {this.result = data.token
            if(this.result) {
            this.$store.state.auth = true
            localStorage.setItem("token", this.result)
        }
        });
        console.log(this.result)
        
      }
   }
}
</script>
