<template>
    <table class="table">
        <thead class="thead-light">
            <tr>
                <th>ID</th>
                <th scope="col">First Name</th>
                <th scope="col">Last Name</th>
                <th scope="col">Salary</th>
                <th scope="col">Age</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(employee, key) in employees" :key="key">
                <th>{{ employee.ID }}</th>
                <td>{{ employee.firstname }}</td>
                <td>{{ employee.lastname }}</td>
                <td>{{ employee.salary }}</td>
                <td>{{ employee.age }} <router-link :to="{name: 'view'}">
                    <button>View</button> 
                    </router-link>
                    <router-link :to="{name: 'edit'}">
                    <button>Edit</button> 
                    </router-link>
                    <button>Delete</button>
                </td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    data() {
        return {
            id: '',
            firstname: '',
            lastname: '',
            salary: '',
            age: '',
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




        

