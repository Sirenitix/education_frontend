<template>
<div>
  <NavBar/>
  <Messenger/>
</div>
</template>


<script>
import NavBar from '~/components/NavBar.vue'
import Messenger from './Messenger.vue'

export default {
components: {
    NavBar,
    Messenger
  },
name: 'HomePage',
  data () {
      return {
        
      }      
    }
}   
</script>
