<template>
  <div id="app">
    <div id="nav">
      <header>
        <nav class="navbar navbar-expand-lg navbar-light bg-light navbar-custom container">
          <div class="logo">
            <img src="../src/assets/logo.png" alt srcset="../src/assets/logo2x.png 2x, ../src/assets/logo3x.png 3x" class="animate__animated animate__bounce" />
          </div>
          <router-link class="navbar-brand" to="/">Главная</router-link>
          <router-link class="navbar-brand" to="/list">Список покупок</router-link>
        </nav>
      </header>
    </div>
    <router-view />
    <hr />
    <Footer />
  </div>
</template>

<script>
import Footer from "./components/Footer";
export default {
  components: {
    Footer
  }
};
</script>
