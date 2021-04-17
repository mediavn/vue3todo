<template>

  <nav class="navbar is-white" role="navigation" aria-label="main navigation">
    <div class="container">
      <div class="navbar-brand">
      <a class="navbar-item" href="#">
        <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
      </a>

      <a role="button" class="navbar-burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
      </div>

      <div id="navbarBasicExample" class="navbar-menu">
      <div class="navbar-start">

        <router-link class="navbar-item" to="/">Home</router-link>
        <router-link class="navbar-item" to="/todos">Todos</router-link>
        
      </div>

      <div class="navbar-end">
        <div class="navbar-item">
          <div class="buttons">
            <a class="button is-primary">
              <strong>Sign up</strong>
            </a>
            <a class="button is-light">
              Log in
            </a>
          </div>
        </div>
      </div>
      </div>
    </div>
  </nav>

   
  <router-view/>
</template>
<script>
 
export default {
  name: 'app',
}
</script>


<style lang="scss">
  @import "~bulma/css/bulma.css";
</style>
