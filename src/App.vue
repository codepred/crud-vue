<template @mouseover="updateLoginButton">
  <div class="vue-template" @mouseover="updateLoginButton">
    <!-- Navigation -->
    <nav class="navbar shadow bg-white rounded justify-content-between flex-nowrap flex-row fixed-top">
      <div class="container">
        <a class="navbar-brand float-left" target="_blank">
        </a>
        <ul class="nav navbar-nav flex-row float-right">
          <li class="nav-item">
            <router-link v-if="showLogoutButton" class="nav-link pr-3" to="/log-in" @click="clearSessionStorage">Wyloguj</router-link>
          </li>
        </ul>
      </div>
    </nav>
    <!-- Main -->
    <div class="App">
      <div class="vertical-center">
        <div class="inner-block">
          <router-view />
        </div>
      </div>
    </div>
  </div>
</template>

<script>

 export default {

        data(){
            return{
                 showLogoutButton: true
            }
        },
        mounted:function() {

            const checkURL = String(window.location.href)
            if (checkURL.includes("log-in")) {
              this.showLogoutButton = false
            }
        },
        methods: {
          updateLoginButton() {
            const checkURL = String(window.location.href)
            if (checkURL.includes("log-in")) {
              this.showLogoutButton = false
            }
            else {
              this.showLogoutButton = true
            }
          },
          clearSessionStorage () {
             localStorage.setItem('username', 'ty kurwo');
          }
      }
 }
  


</script>


<style>

div {
    align-self: center;
    margin-left: auto;
}
.vertical-center{
   position: absolute;
   top: 50%;
   left: 50%;
   transform: translate(-50%, -50%);
}

</style>