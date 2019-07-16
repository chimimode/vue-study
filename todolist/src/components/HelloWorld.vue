<template>
  <div class="full-control">
    <md-list>
      <md-subheader>
        <md-field>
      <label>Type here!</label>
      <md-input v-model="type"></md-input>
      <span class="md-helper-text">새로등록</span>
    </md-field>
      </md-subheader>

      <md-list-item>
        <md-checkbox v-model="notification" value="preview" />
        <span class="md-list-item-text">Show content preview</span>
      </md-list-item>

      <md-list-item>
        <md-checkbox v-model="notification" value="sound" />
        <span class="md-list-item-text">Sound</span>
      </md-list-item>

      <md-list-item>
        <md-checkbox v-model="notification" value="vibrate" />
        <span class="md-list-item-text">Vibrate</span>
      </md-list-item>

      <md-list-item>
        <md-checkbox v-model="notification" value="light" />
        <span class="md-list-item-text">Notification light</span>
      </md-list-item>
    </md-list>
  </div>
</template>

<script>
export default {
  name: 'Controls',
  data: () => ({
    notification: ['sound', 'vibrate']
  })
}
</script>

<style lang="scss" scoped>
  .full-control > .md-list {
    width: 320px;
    max-width: 100%;
    height: 400px;
    display: inline-block;
    overflow: auto;
    border: 1px solid rgba(#000, .12);
    vertical-align: top;
  }
</style>
