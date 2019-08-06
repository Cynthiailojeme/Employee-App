<template>
    <table class="table table-hover">
         <thead class="thead-light">
            <tr>
                <th scope="col">ID</th>
                <th scope="col">Name</th>
                <th scope="col">Salary</th>
                <th scope="col">Age</th>
            </tr>
        </thead>
            <tbody>
                <tr v-if="employee">
                    <td>{{employee.id}}</td>
                    <td>{{ employee.employee_name}}</td>
                    <td>{{employee.employee_salary}}</td>
                    <td>{{employee.employee_age}}</td>
                </tr>

            </tbody>
        </table> 
</template>

<script>
    export default{
        name:'home',
        props: ['id'],
            data() {
                return{
                    apiResponse:{},
                    employee: null,
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
        }
    };
</script>

