<template>
    <header>
        <div class = "center">
            <Button class = "myButton" v-show="homePage" @btn-click="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'red' : 'green'"> </Button>
        </div>    
    </header>
</template>

<script>
import Button from './Button.vue'

    export default{
        name: 'Header',
        props: {
            title: {
                type: String,
                default: '',
            },
            showAddTask: Boolean,
        },
        components: {
            Button
        },
        computed: {
            homePage() {
                if(this.$route.path ==='/'){
                    return true
                } else{
                    return false
                }
            }
        }
    }
</script>

<style scoped>
    header {
        width: 600px;
        position: relative;
        justify-content: space-between;
    }
    .myButton{
        width: 190px;
    }
    .center{
        padding-top: 46px;
        padding-left: 850px;
    }
</style>