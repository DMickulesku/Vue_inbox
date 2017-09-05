<template>
  <div class="row toolbar">
  <div class="col-md-12">

    <b-button class="btn btn-default" @click="bulkSelect">
      <icon v-if="halfCheckbox" name="minus-square-o"></icon>
      <icon v-if="bulkCheckbox" name="check-square-o"></icon>
      <icon v-if="emptyCheckbox" name="square-o"></icon>
    </b-button>

    <b-button class="btn btn-default">
      Mark As Read
    </b-button>

    <b-button class="btn btn-default">
      Mark As Unread
    </b-button>

    <select class="form-control label-select">
      <option>Apply label</option>
      <option value="dev">dev</option>
      <option value="personal">personal</option>
      <option value="gschool">gschool</option>
    </select>

    <select class="form-control label-select">
      <option>Remove label</option>
      <option value="dev">dev</option>
      <option value="personal">personal</option>
      <option value="gschool">gschool</option>
    </select>

    <b-button class="btn btn-default">
      <icon name="trash-o"></icon>
    </b-button>

    <p class="pull-right">
      <b-badge class="badge" pill variant="" name="badge badge">2</b-badge>
      unread messages
    </p>
  </div>
</div>
</template>

<script>
export default {
  name: 'toolbar',
  props: [
    'emails',
    'bulkCheckbox',
    'halfCheckbox',
    'emptyCheckbox',
    'bulkSelect'
  ]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
