<template>
    <div>
        <form @submit.prevent="uploadForm">
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" class="form-control" id="firstname" v-model="name">
                </div>
                <div class="form-group">
                    <label for="salary">Salary</label>
                    <input type="text" class="form-control" id="salary" v-model.number="salary">
                </div>
                <div class="form-group">
                    <label for="age">Age</label>
                    <input type="text" class="form-control" id="age" v-model.number="age">
                </div>
            <center><button type="submit" class="btn btn-primary">SAVE</button></center>
    </form>

    <div class="alert alert-success" v-show="success">
        The database has been updated
    </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: '',
            salary: '',
            age: '',
            success: false
        }
    },
    methods: {
        uploadForm() {
            this.success
            const data = {
                name: this.name,
                salary: this.salary,
                age: this.age
            }
            this.$http.post('http://dummy.restapiexample.com/api/v1/create', data)
            .then(response => {
            this.success = true
            this.name = '' 
            this.salary = '' 
            this.age = '' 
            }, error => console.log(error))
        }
    }
}
</script>


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
