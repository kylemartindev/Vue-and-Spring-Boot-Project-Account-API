<template>
  <div id="app">
    <div id="app">
    <nav class="navbar navbar-dark bg-primary">
      <div class="container">
        <div class="navbar-header">
          <ul class="nav  nav-pills justify-content-center">
            <h1>Accounts System</h1>
               <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#" back-groundcolor="white" role="button" aria-haspopup="true" aria-expanded="false">Accounts</a>
               <div class="dropdown-menu">
              <a class="dropdown-item" href="#" >Add Accounts</a><br>
              <a class="dropdown-item" href="#" v-on:click="getaccount()">Get Accounts</a>
              </div>
            </li>
          </ul>
        </div>
        </div>
      </nav>
    <router-view/>
  </div>
  </div>
</template>

<script>
export default {
  name: 'App'
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
