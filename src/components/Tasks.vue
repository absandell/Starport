<template>
    <div class = "taskblock">
        <div class = "tasklist" :key="task.id" v-for="task in tasks">
            <div class = "outer">
                <Task class = "taskitem" @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task"/>
            </div>        
        </div>
    </div>
</template>

<script>
    import Task from '../components/Task'

    export default{
        name: 'Tasks',
        props: {
            tasks: Array
        },
        components:{
            Task
        },
        emits: ['delete-task', 'toggle-reminder'],
    }
</script>

<style scoped>
    .taskblock{
        padding-top: 100px;
        padding-left: 650px;
    }

    .tasklist{
        width: 600px;
    }

    .outer{
        padding: 10px;
        margin-bottom: 10px;
        background-color: rgb(0,162,232);
        border-radius: 20%;
    } 
    .taskitem{
        border-radius: 5%;
        background-color: rgb(165, 192, 222);
    }
</style>