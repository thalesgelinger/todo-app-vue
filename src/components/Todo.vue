<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <div class="input-task">
      <input type="text" v-model="task" ref="task">
      <button v-on:click="addTask">+</button>
    </div>
    <ul>
      <Task 
        v-for="task in tasks"
        :key="task.id"
        :id="task.id"
        :name="task.name"
        v-on:remove="removeTask"
      />
    </ul>
  </div>
</template>

<script>

import Task from './Task.vue'

export default {
  name: 'Todo',
  components: {
    Task
  },
  data() {
    return {
      title: 'Todo app',
      task: '',
      tasks: []
    }
  },
  methods: {
    addTask() {
      if(this.task) {
        this.tasks.push({
          id: this.tasks.length,
          name: this.task
        })
        this.task = ""
      }
      this.$refs.task.focus()
    },

    removeTask(idTask) {
      this.tasks = this.tasks.filter(({id}) => id !== idTask)
    }

  },
  watch: {
    tasks(val) {
      console.log(val);
    }
  }
}

</script>




























<style>

.container {
  height: 100vh;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  margin-top: 10px;
}

h1 {
  margin: 30px 0;
}

.input-task {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  width: 50%;
  min-width: 350px;
}

.input-task input {
  margin-right: 10px;
  height: 40px;
  flex: 1;
  border: 1px solid #35495E;
  border-radius: 3px;
  padding-left: 10px;
}

ul {
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  margin-top: 20px;
}

button {
  color: white;
  background: #41B883;
  height: 40px;
  width: 40px;
  font-size: 2rem;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  transition: opacity .2s; 
}

button:hover {
  opacity: 0.4;
}

</style>