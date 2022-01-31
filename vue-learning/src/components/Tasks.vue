<template>
    <div>
        <div :key="task.id" v-for="task in tasks">
            
            <Task @toggle-reminder="$emit('toggle-reminder', task.id)" v-on:delete-task="$emit('delete-task', task.id)" :task="task"/>
            
            <!-- <button v-on:click="onClick()" v-bind:style="{ background: color }"  class="btn">{{text}} </button> -->

        </div>
    </div>
</template>

<script>
import Task from './Task'
   export default {
       name: 'Tasks',
       props: {
           tasks: Array
       },
       components: {
           Task,
       },
       emits: ['delete-task', 'toggle-reminder'],
   }
</script>
