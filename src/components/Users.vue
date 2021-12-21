<template>
  <div class="container">
    <h3>Liste des utilisateurs :</h3>
    <table class="table bg-light">
      <thead>
        <tr class="bg-info text-light">
          <th scope="col">Identifiant</th>
          <th scope="col">Nom</th>
          <th scope="col">Email</th>
          <th scope="col">Ville</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" v-bind:key="user.id"> 
          <th scope="row">{{user.id}}</th>
          <td>{{user.name}}</td>
          <td>{{user.email}}</td>
          <td>{{user.address.city}}</td>
        </tr>
      </tbody>
    </table> 
  </div> 
</template>
<script>
  import axios from 'axios';  export default {
    name: 'Users',
    data() {
      return {
        users: null,
      };
    },
    created: function() {
      axios
        .get('https://jsonplaceholder.typicode.com/users')
        .then(res => {
          this.users = res.data;
        })
    }
  }
</script>
<style>
  h3 {
    margin-bottom: 5%;
  }
</style>