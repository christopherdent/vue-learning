<template>
    <div class="container">
      <Header 
      @toggle-add-task="toggleAddTask"
      title="Task Tracker"
       />
      <!-- <div v-if="showAddTask"> tutorial's way to toggle, I did my own-->
      <AddTask @add-task="addTask" />
      <!-- </div> -->
      <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask"
      :tasks="tasks" />
      <Footer />
    </div>
   
</template>





<script>
//import components here 
import Footer from './components/Footer'
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'
///register components below 

export default {
  name: 'App',
  components: {
     Header,
     Tasks,
     AddTask,
     Footer
      
  },
///data causes components to render 
  data() {
    return {
      // showAddTask: false  //tutorial way for toggle 
      tasks: []
    }
  },
  methods: {
    // toggleAddTask(){
    //   this.showAddTask = !this.showAddTask
    // },  ///this method was tutorial's way to toggle. mine works fine although this is the more 'vue' way to do it.
    addTask(task){
      this.tasks = [...this.tasks, task]
    },

    deleteTask(id) {
     
      console.log('task', id)
    if(confirm("are you sure")){
      this.tasks = this.tasks.filter((task) => task.id !== id)     
      }
    },
    toggleReminder(id) {
      console.log(id)
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task) 

    }
  },

  created() {
    //typically an http request would go here, for now just hardcoding
    ///request might look like this.tasks = this.fetchTasks()
    this.tasks = [
      {
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      {id: 2,
      text: 'meeting at school',
      day: 'March 2 at 1:30pm',
      reminder: true,
      
      },
      {
        id: 3,
        text: 'food shopping',
        day: ' March 17 at 4:00pm',
        reminder: false,
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
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}


.btn {
  display: inline-block;
  background: green;
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

.btn-cancel {
  display: inline-block;
  background: red;
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
