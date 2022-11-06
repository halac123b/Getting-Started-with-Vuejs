<template>
  <div class="app">
    <h2 :class={selection:selected}>Welcome to Vuejs</h2>
    <input type="text" v-model="name" :disabled="isDisable">
    <TestNow />
    <div v-show="isShow">{{ name }}</div>
    <button @click="isShow=!isShow, isDisable=!isDisable, selected=!selected">
      Show/Hide
    </button>
    <hr>
    <div v-bind:id="id"></div>
    <div v-for="(task, index) in tasks" :key="index">
      <input type="checkbox" v-model="task.done">
      <span :class="{complete:task.done}">{{ task.content }}</span>
    </div>
    <input type="text" v-model="newTask">
    <button @click="addTask()">Add task</button>
    <hr>
    <TaskData v-for="(task, index) in tasks" :key="index" :taskData="task"/>
    <hr>
    <MultiSelect />
    <hr>
    <div>{{ formatMoney }}</div>
    <button @click="sumMoney += 20000">Donate</button>
  </div>
</template>

<script>
import TestNow from './components/Test.vue'
import TaskData from './components/Task.vue'
import MultiSelect from './components/MultiSelect.vue'

export default {
  name: 'App',
  data() {
    return {
      name: 'nguyen duy ha',
      isShow: true,
      id: 'gacon',
      isDisable: false,
      selected: true,
      tasks: [
        { content: 'code', done: false },
        { content: 'movie', done: false },
        { content: 'music', done: false },
        { content: 'housework', done: false }
      ],
      sumMoney: 1000000
    }
  },
  methods: {
    addTask: function(){
      this.tasks.push({content:this.newTask, done:false});
      this.newTask = '';
    }
  },
  watch: {
    newTask: function(newValue, oldValue){
      console.log(oldValue);
      console.log(newValue);
    }
  },
  computed: {
    formatMoney: function(){
      return this.sumMoney.toFixed(2).replace(/\d(?=(\d{3})+\.)/g,'$&,');
    }
  },
  components: {
    TestNow,
    TaskData,
    MultiSelect
  }
}
</script>

<style>
  .selection {
    color: red;
  }
  .complete {
    text-decoration: line-through;
  }
</style>
