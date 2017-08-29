<template>
  <div class="messagebox">
  <div class="row message" :class="{read: hasRead, unread: !hasRead, selected: selected, unselected: !selected}">
  <div class="col-xs-1">
    <div class="row">
      <div class="col-xs-2">
        <input class="checkbox" type="checkbox" v-model="checked"/>
      </div>
      <div class="col-xs-2">
        <icon v-if="!stars" class="star" name="star-o" v-model="stars"></icon>
        <icon v-if="stars" class="star" name="star" v-model="stars"></icon>
      </div>
    </div>
  </div>
  <div class="col-xs-11">
    <b-badge class="label" variant="warning" v-for="label in labels">{{ label }}</b-badge>
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
  }
}
</script>

<style lang="css">
</style>
