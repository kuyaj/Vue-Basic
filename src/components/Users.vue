<template>
    <div id="registration">
        <h3>Users</h3>
        <h5> {{ numberOfUsers }}</h5>
        <hr>
        <div class="row" v-for="(user, key) in users" :key="key">
            <h4>{{ user.name }}</h4>
            <button @click="registerUser(user)">Register</button>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['users', 'keyword'],
        methods: {
            registerUser(user) {
                this.$emit('userRegistered', user);
                user.registered = true;
            }
        },
        computed: {
            numberOfUsers(){
                return this.users.length;
            },
            filteredUsers(){

            }
        }
    }
</script>

<style scoped>
    #registration {
        box-shadow: 1px 1px 2px 1px #ccc;
        margin: 20px;
        padding: 20px;
        display: inline-block;
        width: 350px;
        vertical-align: top;
    }


    h3 {
        color: #303952;
    }

    .row h4 {
        display: inline-block;
        width: 70%;
        text-align: left;
        margin: 0 0 10px 0;
    }

    button {
        background-color: #00b894;
        border: transparent;
        border-radius: 2px;
        text-align: right;
        font-family: inherit;
        font-size: 14px;
        cursor: pointer;
        padding: 5px;
        color: white;
        outline: none;
    }

    button:hover {
        background-color: #0984e3;
    }
</style>