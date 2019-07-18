<template>
  <div class="full-control">
    <div>
      <span class="md-display-3" id="clock"></span>
    </div>
    <md-list>
      <md-subheader>
        <md-field>
      <label>Type here!</label>
      <md-input v-model="todo" @keyup.enter="add"></md-input>
      <span class="md-helper-text">새로등록</span>
    </md-field>
      </md-subheader>

      <my-component></my-component>

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
    notification: ['sound', 'vibrate'],
    test: new Date()
  }),
  methods: {
    add: function (event) {
      console.log(this)
      console.log(this.todo)
    },
    clock: function () {
      return nowTime()
    }
  }
}

function nowTime () {
  let now = new Date()
  let ampm = now.getHours() > 12 ? 'PM' : 'AM'
  let hour = now.getHours() > 12 ? now.getHours() - 12 : now.getHours()
  hour = hour < 10 ? `0${hour}` : hour
  let min = now.getMinutes() < 10 ? `0${now.getMinutes()}` : now.getMinutes()
  let sec = now.getSeconds() < 10 ? `0${now.getSeconds()}` : now.getSeconds()

  document.getElementById('clock').textContent = `${ampm} ${hour}:${min}:${sec}`
}

setInterval(nowTime, 1000)
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
