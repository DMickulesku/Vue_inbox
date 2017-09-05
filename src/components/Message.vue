<template>
  <div class="messagebox">
  <div class="row message" :class="{read: email.read, selected: this.email.selected}">
  <div class="col-xs-1">
    <div class="row">
      <div class="col-xs-2">
        <input @click="emailChecked" class="checkbox" type="checkbox" v-model="checked"/>
      </div>
      <div class="col-xs-2" @click="emailStarred()">
        <icon v-if="!email.starred" class="star" name="star-o"></icon>
        <icon v-else class="star" name="star"></icon>
      </div>
    </div>
  </div>
  <div class="col-xs-11">
    <b-badge class="label" variant="warning" v-for="label in labels" key="">{{ label }}</b-badge>
    <a href="#">
      {{ email.subject }}
    </a>
  </div>
</div>
</div>
</template>

<script>
export default {
  name: 'email',
  props: ['email'],
  data () {
    return {
      hasRead: this.email.read,
      selected: this.email.selected,
      checked: this.email.selected,
      stars: this.email.starred,
      labels: this.email.labels
    }
  },
  methods: {
    emailStarred() {
      this.email.starred = !this.email.starred
    },
    emailChecked() {
      this.email.selected = !this.email.selected
    }
  }
}

</script>

<style lang="css" scoped>
  
</style>
