<template>
    <table class="table">
        <thead class="thead-light">
            <tr>
                <th scope="col">ID</th>
                <th scope="col">Name</th>
                <th scope="col">Salary</th>
                <th scope="col">Age</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(employee, key) in employees" :key="key">
                <th>{{ employee.id }}</th>
                <td>{{ employee.employee_name }}</td>
                <td>{{ employee.employee_salary }}</td>
                <td>{{ employee.employee_age }} 
                    <router-link :to="{name:'view', params:{id: employee.id}}">
                    <button>View</button> 
                    </router-link>
                    <router-link :to="{name:'edit',params:{id: employee.id}}">
                    <button>Edit</button> 
                    </router-link>
                    <button @click.prevent="del(employee)">Delete</button>
                </td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    data() {
        return {
            employees: []
        }
    },
    created: function()
      {
          this.fetchEmployees();
      },
    methods: {
        fetchEmployees(){
          {
              this.$http.get('http://dummy.restapiexample.com/api/v1/employees').then((response) => {
                console.log(response.body);
                  this.employees = response.body;
              });
          }
        },
        del: function(employee){
            if (confirm("do you want to delete?")) {
                this.$http.delete('http://dummy.restapiexample.com/api/v1/delete/'+employee.id)
                .then(response=>{
                 console.log(response)
                     alert("record sucessfully deleted")
            })
         }
        }
      }
    }
</script>

<style scoped>
     button {
       background: #ffffff;
        border-radius: 5px;
    }
</style>




        

