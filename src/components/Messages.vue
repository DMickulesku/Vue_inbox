<template>
  <div class="messages">
    <Message v-for='email in emailList' :email='email' key='' :emailStarred='emailStarred' :staro='staro' :star='star'></Message>
  </div>
</template>

<script>
import Message from './Message'
import Data from '../data/seeds'

export default {
  name: 'messages',
  props: [ 'email','emailStarred', 'staro', 'star'],
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
