import 'bootstrap/dist/css/bootstrap.css'

<template>
  <div class="home">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="#">My App</a>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <nuxt-link to="/card" class="nav-link">Card</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link to="/serviceform" class="nav-link">Form</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link to="/mychallenges" class="nav-link">About my challenges</nuxt-link>
          </li>
        </ul>
      </div>
    </nav>

    <div class="container mt-4">
      <nuxt />
    </div>
  </div>
</template>

<style scoped>
.home {
  height: 100vh;
}

/* Опціонально залиште стилізацію вашого списку */
/* .header {
  display: flex;
  gap: 30px;
  list-style: none;
}

.listItem {
  font-size: 20px;
} */
</style>
