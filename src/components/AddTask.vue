<template>
  <form @submit.prevent="addTaskSubmit" class="card" >
    <div class="card-body">
    <div class="form-group">
      <label class="text-danger">Task Name</label>
      <input class="form-control" type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Task Time & Date</label>
      <input type="text" v-model="day" name="day"
        placeholder="Add date"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
    </div>
  </form>
</template>

<script>
export default{
    name: 'AddTask',
    data(){
        return{
            text:'',
            day:'',
            reminder: false
        }
    },
    methods:{
        addTaskSubmit(){
           if(!this.text){
               alert('Please enter a task')
               return
           }
           
           const newTask = {
               id: Math.floor(Math.random() * 100),
               text: this.text,
               day: this.day,
               reminder: this.reminder,
               

           }
           
           this.$emit('add-task', newTask)
           //console.log(newTask)
           this.text=''
           this.day=''
           this.reminder='false'
        }
    }
}
</script>

<style scoped>
</style>



