<template>
  <div class="messagebox">
  <div class="row message" :class="{read: hasRead, unread: !hasRead, selected: selected, unselected: !selected}">
  <div class="col-xs-1">
    <div class="row">
      <div class="col-xs-2">
        <input class="checkbox" type="checkbox" v-model="checked"/>
      </div>
      <div v-on:click="emailStarred" class="col-xs-2">
        <icon v-if="!email.starred" class="star" v-bind:name="staro"></icon>
        <icon v-if="email.starred" class="star" v-bind:name="star"></icon>
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
  props: ['email', 'staro', 'star', 'emailStarred'],
  data () {
    return {
      hasRead: this.email.read,
      selected: this.email.selected,
      checked: this.email.selected,
      stars: this.email.starred,
      labels: this.email.labels
    }
  }
}

</script>

<style lang="css">
</style>
