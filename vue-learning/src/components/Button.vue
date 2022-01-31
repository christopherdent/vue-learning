<template>
    <button id="add-button" v-on:click="onClick()" v-bind:style="{ background: color }"  class="btn">{{text}} </button>
    <!-- with shortcuts <button @click="onClick()" :style="{ background: color }"  class="btn">{{text}} </button> -->
</template>


<script>
    
    export default {
        name: 'Button',
        props: {
            text: String,
            // color: String
        },
        methods: {
            onClick() {

                // this.$emit('toggle-add-task')   ///tutorial way to do below

                let form = document.getElementById('form')
                let button = document.getElementById('add-button')
                if (!form.hidden) {  //if form not hidden
                    form.hidden = true;
                    button.innerText = "add task";
                    button.classList.remove('btn-cancel');
                    button.classList.add('btn');

                } else {
                    form.hidden = false;                     
                    button.innerText = "cancel";
                    button.classList.remove('btn');
                    button.classList.add('btn-cancel');
                }
            }
        }
    }

</script>

