<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1></h1>
    <user-list></user-list>
  </div>
</template>

<script>
import UserList from './UserList.vue';
import io from 'socket.io-client';

export default {
  name: 'app',
  components: {'user-list': UserList},
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  created() {
    var socketio = io('http://localhost:24602');
    socketio.on('turn', (data) => {
      console.log(data);
    });
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
