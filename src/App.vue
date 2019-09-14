<template>
  <div id="app">
    <add-users @addUser="addUser"></add-users>
    <app-users @userRegistered="userRegistered" :users="unregisteredUsers"></app-users>
    <app-registered @userUnregistered="userUnregistered" :registrations="registrations"></app-registered>
  </div>
</template>

<script>
  import Users from './components/Users.vue';
  import Registered from './components/Registered.vue';
  import AddUser from './components/AddUser.vue';

export default {
    data() {
        return {
            registrations: [],
            users: [
                {id: 1, name: 'Max', registered: false},
                {id: 2, name: 'Anna', registered: false},
                {id: 3, name: 'Chris', registered: false},
                {id: 4, name: 'Sven', registered: false},
                {id: 5, name: 'Erric', registered: false}
            ],
            search_user: ""
        }
    },
    computed: {
        unregisteredUsers() {
            return this.users.filter((user) => {
                return !user.registered;
            });
        },
    },
    methods: {
      userRegistered(user) {
          const date = new Date;
          this.registrations.push({
            userId: user.id, 
            name: user.name, 
            date: date.getMonth() + '/' + date.getDay()
          })
      },
       userUnregistered(registration) {
          const user = this.users.find(user => {
              return user.id == registration.userId;
          });
          user.registered = false;
          this.registrations.splice(this.registrations.indexOf(registration), 1);

        },
        addUser(user){  
          let id = this.users.length+1;
          this.users.push({
            id:id,
            name: user,
            registered: false 
          })
        }
    },
    components: {
        appUsers: Users,
        appRegistered: Registered,
        addUsers: AddUser
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Gayathri&display=swap');
#app {
   font-family: 'Gayathri', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
