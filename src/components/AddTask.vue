<template>
<div class = "formBox">
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input type="text" v-model="text" name="text" placeholder="Add Task" />
        </div>
        <div class="form-control">
            <label>Description</label>
            <input type="text" v-model="description" name="description" placeholder="Add Description" />
        </div>
        <div class="form-control">
            <label>Time Due</label>
            <input type="datetime-local" v-model="day" name="day" placeholder="Enter Time" />
        </div>
        <div class="form-control form-control-check">
            <label>Set Reminder</label>
            <input type="checkbox" v-model="reminder" name="reminder" />
        </div>
        <input type="submit" value="Save Task" class="btn btn-block" />
    </form>
</div>
</template>

<script>
    export default{
        name: 'AddTask',
        data(){
            return {
                text: '',
                description: '',
                date: '',
                reminder: false,
            }
        },
        methods: {
            onSubmit(e){
                e.preventDefault()

                if(!this.text){
                    var errorAudio = new Audio(require('../assets/sweep.wav'))
                    errorAudio.play()
                    alert('Please Enter a Task')
                    return
                }

                const newTask = {
                    text: this.text,
                    description: this.description,
                    day: this.day,
                    reminder: this.reminder,
                }

                this.$emit('add-task', newTask)
                
                console.log("here")
                var submitAudio = new Audio(require('../assets/OS.wav'))
                submitAudio.play()

                this.text = ''
                this.description = ''
                this.day = ''
                this.reminder = false
            }
        }
    }
</script>

<style scoped>
    .formBox{
        top: 25%;
        left: 1275px;
        position: absolute;
        padding: 10px;
        background-color:rgb(0,162,232);
        border-radius: 10px;
        
    }
    .add-form {
        width: 550px;
        background-color: rgb(165, 192, 222);
        border-color: rgb(0,162,232);
        padding: 10px;
    }
    .form-control {
        margin: 20px 20px;

    }
    .form-control label {
        display: block;
    }
    .form-control input {
        width: 100%;
        height: 40px;
        margin: 5px;
        padding: 3px 7px;
        font-size: 17px;
    }
    .form-control-check {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .form-control-check label {
        flex: 1;
    }
    .form-control-check input {
        flex: 2;
        height: 20px;
    }
</style>