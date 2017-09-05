<template>
  <div class="messages">
    <Message v-for='email in emailList' :email='email' key='email.id'></Message>
  </div>
</template>

<script>
import Message from './Message'
import Data from '../data/seeds'

export default {
  name: 'messages',
  components: {
    Message
  },
  data() {
    return{
      emailList: Data
    }
  }
}
</script>

<style lang="css">

</style>
