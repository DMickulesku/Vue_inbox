<template>
  <div class="row message unread">
  <div class="col-xs-1">
    <div class="row">
      <div class="col-xs-2">
        <input type="checkbox" />
      </div>
      <div class="col-xs-2">
        <i class="star fa fa-star-o"></i>
      </div>
    </div>
  </div>
  <div class="col-xs-11">
    <a href="#">
      {{ email.subject }}
    </a>
  </div>
</div>
</template>

<script>
export default {
  name: 'email',
  props: ['email']
}
</script>

<style lang="css">
</style>
