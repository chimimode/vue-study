<template>
  <div class="full-control">
    <div>
      <span class="md-display-3" id="clock"></span>
    </div>
    <md-list id="items">
      <md-subheader>
        <md-field>
          <label>Type here!</label>
          <md-input v-model="todoItem" @keyup.enter="add"></md-input>
          <span class="md-helper-text">새로등록</span>
        </md-field>
        <md-button class="md-raised md-accent" v-on:click="add">추가</md-button>
      </md-subheader>

      <md-list-item>
        <md-checkbox v-model="notification" value="preview" />
        <span class="md-list-item-text">sample data</span>
      </md-list-item>

      <md-list-item v-for="(todo, i) in todos" :key="i" >
        <md-checkbox v-model="notification" value="i" />
        <span class="md-list-item-text">{{ todo }}</span>
        <md-button class="md-raised md-accent" v-on:click="del">삭제</md-button>
      </md-list-item>
    </md-list>
  </div>
</template>

<script>
export default {
  name: 'Controls',
  data: () => ({
    notification: ['sound', 'vibrate'],
    counter: 0,
    todoItem: null,
    todos: []
  }),
  methods: {
    add: function (event) {
      if (this.todoItem !== undefined) {
        this.todos.push(this.todoItem)
      }
    },
    del: function (event) {
      console.log('삭제 완성하고싶다긔')
      this.todos.splice(0, 1)
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
