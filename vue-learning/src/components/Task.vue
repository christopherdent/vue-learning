<template>
<div 
    @dblclick="$emit('toggle-reminder', task.id)" 
    :class="[task.reminder ? 'reminder' : '', 'task']"
    
    >
    
    
    <h3>{{ task.text }}

        <i @click ="$emit('delete-task', task.id)" class = 'fas fa-times'></i>
    </h3>
    <p>{{ task.day }}</p>
  
</div>

</template>


<script>

    export default {
        name: 'Task',
        props: {
            task: Object,
        },
        methods: {     ///some methods can be done right in the tags instead of below
        //emit lets you pass props up 
        // onDelete(id) {
        //     // debugger; // eslint-disable-line no-debugger
        //     // console.log('task', id)   --- id still correct here 
        //     this.$emit('delete-task', id)
        // }

    }
}

</script>



<style>
.fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}



</style>