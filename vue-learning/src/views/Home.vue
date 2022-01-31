<template>
    <div>
        <AddTask 
        @add-task="addTask" 
        />
                         
        <Tasks 
        @toggle-reminder="toggleReminder" 
        @delete-task="deleteTask"
        :tasks="tasks" 
        />
    </div>
</template>


<script>
    import Tasks from '../components/Tasks'
    import AddTask from '../components/AddTask'


    export default {
        name: 'Home',
        components: {
            Tasks, 
            AddTask,
        },
        data() {   ///data is like state 
            return {
            tasks: [],
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
           if(confirm("are you sure")){
             this.tasks = this.tasks.filter((task) => task.id !== id)     
           }
         },
        toggleReminder(id) {          
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
