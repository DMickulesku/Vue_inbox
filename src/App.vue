<template>
  <div id="app">
    <toolbar
      :emails='emails'
      :bulkCheckbox='bulkCheckbox'
      :halfCheckbox='halfCheckbox'
      :emptyCheckbox='emptyCheckbox'
      :unreadCount='unreadCount'
      :bulkSelect='bulkSelect'
      :removeMessage='removeMessage'>

    </toolbar>

    <messages
      :emails='emails'
      :starred='starred'>
    </messages>

    <br>
    <!-- <compose
      :inputForm='inputForm'
      :exitForm='exitForm'
      :form='form'>
    </compose> -->
  </div>
</template>

<script>
import Toolbar from './components/Toolbar'
import Message from './components/Message'
import Messages from './components/Messages'
import Compose from './components/Compose'
// import data from './data/seeds'

const baseURL= 'http://localhost:8082/api'

export default {
  name: 'app',
  components: {
    Toolbar,
    Message,
    Messages,
    Compose
  },
  data() {
    return {
      form: false,
      emails: []
    }
  },
  methods: {
    starred() {
      return true;
    },
    bulkSelect() {
      if (this.bulkCheckbox) {
        this.emails.forEach(email => this.$set(email, 'selected', false))
      } else {
        this.emails.forEach(email => this.$set(email, 'selected', true))
      }
    },
    removeMessage() {
      this.emails = this.emails.filter(email => {
        return !email.selected
      })
    }

  },
  computed: {
    unreadCount() {
      return this.emails.reduce((acc, email) => {
        if (email.read == false) {
          acc++
        }
        return acc
      }, 0)
    },
    bulkCheckbox() {
      return this.emails.every(email => email.selected)
    },
    halfCheckbox() {
      return this.emails.some(email => email.selected) && !this.bulkCheckbox
    },
    emptyCheckbox() {
      return this.emails.every(email => !email.selected)
    }

  },
  async mounted() {
    const data = await fetch(`${baseURL}/messages`)
    const response = await data.json()
    this.emails = response._embedded.messages.map(message => {
      message.selected = false
      return message
    })
  }
}

</script>

<style>
#app {
  font-family: ‘Avenir’, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-left: 5em;
  color: #2c3e50 ;
  margin-top: 60px;
}

.pull-right {
  display: inline-block;
  margin-left: 10%;
}

.messagebox {
  margin-left: 2em;
}

.checkbox {
  margin-left: 1.5em;
  margin-right: 2em;
}

.star {
  margin-right: 2em;
}

.message {
  margin-left: 0px;
  padding-top: 8px;
  padding-bottom: 8px;
  cursor: pointer;
  border-bottom: 1px solid #efefef ;
}

.row {
    margin-right: -15px;
}

.message a {
  color: black;
}

.message a:hover, .message a:active, .message a:focus {
  text-decoration: none;
}

.message + .message {
  border-top: 1px solid #efefef ;
}

.message.read {
  background: #efefef ;
}

.message.unread {
  font-weight: bold;
}

.message.selected {
  background: #ffffcc ;
}

.message:hover {
  margin-left: -3px;
  border-left: 3px solid #ccc;
}

.message-body {
  background: #ccc;
  margin-left: 0;
  margin-bottom: 1em;
  padding-top: 1em;
  padding-bottom: 1em;
}

.toolbar {
  margin-left: 1em;
  margin-top: 1em;
  margin-bottom: 1em;
}

.toolbar .label-select {
  width: auto;
  display: inline;
}

.toolbar select,
.toolbar button,
.toolbar a,
.toolbar .badge {
  margin-right: .5em;
  margin-bottom: .5em;
}

footer.spacer {
  margin-bottom: 20em;
}

.label {
  margin-right: .5em;
}

.fa-close {
  cursor: pointer;
}

.form-horizontal {
  margin-left: 1em;
}
</style>
