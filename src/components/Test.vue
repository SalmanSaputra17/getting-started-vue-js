<template>
    <div class="test">

        <input type="text" v-model="title"><br>
        <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="hitEnter" placeholder="Lihat console browser !">
        <h1>{{title}}</h1>
        <p v-text="body"></p>
        <p v-if="showName">{{user.firstName}} {{user.lastName}}</p>
        <p v-else>Nama anda tidak ditampilkan</p>
        
        <button v-on:click="greet(user.firstName)">Say Greeting</button>

        <br>
        <br>

        <label for="firstName">first name</label>
        <input type="text" id="firstName" v-model="user.firstName"><br>

        <label for="lastName">last name</label>
        <input type="text" id="lastName" v-model="user.lastName"><br>

        <h3>{{fullName}}</h3>

        <p>{{msg}}</p>

    </div>
</template>

<script>
export default {
    name: 'test',
    props: {
        msg: {
            type: String,
            default: 'Ini adalah components properties'
        }
    },
    data() {
        return {
            title: 'Hello World !',
            body: 'This is my first Vue App',
            user: {
                firstName: 'Salman',
                lastName: 'Saputra'
            },
            showName: false,
            items: [
                {title: 'Item One'},
                {title: 'Item Two'},
                {title: 'Item Three'}
            ]
        }
    },
    methods: {
        greet: function(firstName) {
            alert('Good Morning !, ' + firstName);
        },
        pressKey: function(e) {
            console.log(e.target.value);
        },
        hitEnter: function() {
            console.log('Tombol enter ditekan, hmmm');
        }
    },
    computed: {
        fullName: function() {
            return this.user.firstName + ' ' + this.user.lastName;
        }
    }
}
</script>

<style scoped>
</style>

