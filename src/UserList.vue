<template>
  <div id="user-list">
    <div v-for="user in userList">{{user.name}}</div>
  </div>
</template>

<script>
export default {
  name: 'user-list',
  data () {
    return {
      userList: []
    }
  },
  created() {
    console.log('test');
    fetch('http://localhost:24601/users')
    .then((res) => res.json())
    .then((json) => { console.log(json); return json; })
    .then((json) => { this.userList = json; });
  }
}
</script>

<style>
</style>
