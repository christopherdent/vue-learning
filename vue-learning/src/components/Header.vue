<template>

    <div class="header">
    
        <h1>  

            {{ title }}

        </h1>
        <Button 
        @toggle-add-task = "$emit('toggle-add-task')"
        text = 'add task'
         
        
        />

       

   </div> 

</template>


<script>
import Button from './Button'

 export default {
     name: 'Header',
     props: {
         title: String,
      },
      components: {
          Button
      }
    }
</script>



<style scoped>
    header {
        display: flex; 
        justify-content: space-between;
        align-items: center;
        margin-block: 20px;
    }
</style>