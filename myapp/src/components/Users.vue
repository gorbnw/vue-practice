<template>
  <div class="users">
    <h1>Users</h1>
    <form v-on:submit="addUser">
      <input type="text" v-model="newUser.name" placeholder="Enter Name">
      <input type="text" v-model="newUser.email" placeholder="Enter Email">
      <input type="submit" value="Submit">
    </form>
    <ul>
      <li v-for="user in users">
        <input type="checkbox" class="toggle" v-model="user.contacted">
        <span :class="{contacted: user.contacted}">
          {{user.name}}: {{user.email}} <button v-on:click="deleteUser(user)"></button>
        </span>
      </li>
    </ul>

  </div>
</template>

<script>
  export default {
    name: 'users',
    data() {
      return {
        newUser: {

        },
        users: [
          {
            name: 'Peter Piper',
            email: 'pp@gmail.com',
            contacted: false
          },
          {
            name: 'Dog Master',
            email: 'dm@gmail.com',
            contacted: false
          },
          {
            name: 'Garry Larry',
            email: 'gl@gmail.com',
            contacted: false
          },
        ]

      }
    },
    methods: {
      addUser: function(e){
        e.preventDefault();
        this.users.push({
          name: this.newUser.name,
          email: this.newUser.name,
          contacted: false,
        });
      },
      deleteUser: function(user){
        this.users.splice(this.users.indexOf(user), 1);
      }

    },
  }
</script>

<style scoped>
  .contacted{
    text-decoration: line-through;
  }
</style>
