<template>
    <div id="addUser">
         <div class="summary">
            <h3>Add User</h3>
            <h5> {{ username }} </h5>
            <hr>
        </div>
        <div class="row">
            <input type="text" v-model="username" placeholder="name">
            <button @click="addUser"> Add </button>
        </div>
    </div>
</template>
<script>
    export default {
        data(){
           return {
               username: "",
           }
        },
        methods: {
            addUser() {
                this.$emit('addUser', this.username);
                this.username = "";
            },
        },
    }
</script>

<style scoped>
    #addUser {
        box-shadow: 1px 1px 2px 1px #ccc;
        margin: 20px;
        padding: 20px;
        display: inline-block;
        width: 350px;
        vertical-align: top;
        text-align: left;
    }

    button {
        background-color: #0984e3;
        border: transparent;
        border-radius: 2px;
        text-align: right;
        font-family: inherit;
        cursor: pointer;
        padding: 5px;
        color: white;
        outline: none;
    }

    .row input {
        min-width: 97%;
        border: solid 1px #7f8c8d;
        font-size: 16px;
        margin-bottom: 5px;
        font-family: inherit;
        outline: none;
        color: #303952;
    }

    input[type="text"] {
        padding: 3px;
    }

  

    .summary {
        text-align: center;
    }

    h3 {
        color: #303952;
    }

    .row h4 {
        display: inline-block;
        width: 30%;
        margin: 0 0 10px 0;
        box-sizing: border-box;
    }

   
</style>