<template>
  <div class="full-control">
    <div>
      <span class="md-display-3" id="clock"></span>
    </div>
    <md-list id="items">
      <md-subheader>
        <md-field>
          <md-select v-model="level" name="level" id="level" placeholder="중요도">
            <md-option value="중요함">중요함</md-option>
            <md-option value="보통임">보통임</md-option>
            <md-option value="안중요함">안중요함</md-option>
          </md-select>
        </md-field>

        <md-field>
          <label>Type here!</label>
          <md-input v-model="todoItem" @keyup.enter="add"></md-input>
          <span class="md-helper-text">새로등록</span>
        </md-field>
        <md-button class="md-raised md-accent" v-on:click="add">추가</md-button>
      </md-subheader>

      <md-list-item v-for="(todo, index) in todos" :key=index >
        <md-checkbox v-model="checkList" :value=index />
        <span class="md-list-item-text">{{ todo }}</span>
        <md-button class="md-icon-button md-raised" v-on:click="del(index)">
          <md-icon>delete</md-icon>
        </md-button>
      </md-list-item>
    </md-list>
  </div>
</template>

<script>
export default {
  name: 'Controls',
  data: () => ({
    checkList: [],
    level: [],
    counter: 0,
    todoItem: null,
    todos: []
  }),
  methods: {
    add: function (event) {
      if (this.valid()) {
        if (this.todoItem !== undefined) {
          this.todos.push(`${this.level}: ${this.todoItem}`)
        }
      } else {
        alert('내용을 입력 해 주세요')
      }
    },
    valid: function () {
      const level = this.level
      const todo = this.todoItem
      return level !== null && todo !== null
    },
    del: function (event) {
      this.todos.splice(event, 1)
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
