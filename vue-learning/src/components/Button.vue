<template>
    <button id="add-button" v-on:click="onClick()" v-bind:style="{ background: color }"  class="btn">{{text}} </button>
    <!-- with shortcuts <button @click="onClick()" :style="{ background: color }"  class="btn">{{text}} </button> -->
</template>


<script>
    
    export default {
        name: 'Button',
        props: {
            text: String,
            color: String
        },
        methods: {
            onClick() {
                console.log('clicked')
                let form = document.getElementById('form')
                let button = document.getElementById('add-button')
                if (!form.hidden) {
                    form.hidden = true;
                    button.innerText = "add task";
                } else {
                    form.hidden = false; 
                    button.innerText = "Cancel"
                }
            }
        }
    }

</script>
