<template>
    <div>
        <form @submit.prevent="update">
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" class="form-control" id="firstname" v-model="employee.employee_name">
                </div>
                <div class="form-group">
                    <label for="salary">Salary</label>
                    <input type="text" class="form-control" id="salary" v-model.number="employee.employee_salary">
                </div>
                <div class="form-group">
                    <label for="age">Age</label>
                    <input type="text" class="form-control" id="age" v-model.number="employee.employee_age">
                </div>
            <center><button type="submit" class="btn btn-primary">SAVE</button></center>
    </form>

    <div class="alert alert-success" v-show="success">
        This employee's profile has been updated
    </div>
    </div>
</template>

<style scoped>
    form {
        margin: auto;
        padding: 50px;
    }
     button {
       background: #ffffff;
        border-radius: 5px;
        width: 100px;
        height: 40px;
        color: #148489;
    }
    
</style>

<script>
    export default{
        name:'home',
    data() {
        return{
            apiResponse:{},
            employee: {},
            success: false,
            error:{}
         }
    },
    components:{},
        mounted() {
            let id = this.$route.params.id
            this.$http.get('http://dummy.restapiexample.com/api/v1/employee/'+id)
            .then(response =>{
            console.log(response)
            this.employee = response.data
            console.log(this.employee)
        })
    },
    methods:{
        update: function(){
            this.success = true
            this.$http.put('http://dummy.restapiexample.com/api/v1/update/'+this.employee.id,this.employee)
            .then(response=>{
            console.log(response)
        }) 
    }
}
};










</script>