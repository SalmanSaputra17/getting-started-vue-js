<template>
    <div class="users">
        <h1>Input User</h1>
        
        <form v-on:submit="addUser">
            <label for="name">Your Name</label>
            <input type="text" id="name" v-model="newUser.name"> 
            
            <br>
            <br>
            
            <label for="email">Your Email</label>
            <input type="text" id="email" v-model="newUser.email">

            <br>
            <br>

            <button type="submit">Submit</button>
        </form>

        <h1>Users List</h1>

        <!-- <p v-for="user in users">
            <input type="checkbox" class="toggle" v-model="user.contacted">
            <span :class="{contacted: user.contacted}">
                {{user.name}}, {{user.email}}
            </span>
            <button v-on:click="deleteUser(user)">x</button>
        </p> -->

    </div>
</template>

<script>
export default {
    name: 'users',
    data() {
        return {
            newUser: {},
            users: []    
        }
    },
    methods: {
        addUser: function(e) {
            this.users.push({
                name: this.newUser.name,
                email: this.newUser.email,
                contacted: false
            });
            e.preventDefault();
        },
        deleteUser: function(user) {
            this.users.splice(this.users.indexOf(user), 1);
        }
    },
    created: function() {
        this.$http.get('https://jsonplaceholder.typicode.com/users').then(function(response) {
                this.users = response.data;
            });
    }
}
</script>

<style scoped>
.contacted{
    color: green;
}
</style>

