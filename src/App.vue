<template>
  <div class="container">
<!--    <h1>Hello World</h1>-->
    <Header title="Task Tracker"/>
    <AddTask />
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" v-bind:tasks="tasks" />
  </div>
</template>

<script>
import Header from "@/components/Header";
import Tasks from "@/components/Tasks";
import AddTask from "@/components/AddTask";
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    }
  },
  data() {
    return {
      tasks: []
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 1st at 2:30pm',
        reminder: true
      },
      {
        id: 2,
        text: 'Meeting at School',
        day: 'March 2nd at 2:30pm',
        reminder: false
      },
      {
        id: 3,
        text: 'Meeting at restaurant',
        day: 'March 2nd at 8:30pm',
        reminder: true
      }
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 600px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
