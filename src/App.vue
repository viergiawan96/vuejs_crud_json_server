<template>
  <div id="app">
    <div class="navbar navbar-expand-lg navbar-light bg-light" id="nav">
      <a class="navbar-brand" href="/"><router-link to="/">VueCrud</router-link></a>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav" id="cs">
            <li class="nav-item">
              <a class="nav-link"><router-link to="/">Home</router-link><span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item">
              <a class="nav-link"><router-link to="/siswa">Karyawan</router-link></a>
            </li>
            <li class="nav-item">
              <a class="nav-link"><router-link to="/about">About</router-link></a>
            </li>
          </ul>
        </div>
    </div>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#cs a.router-link-exact-active {
  color: #42b983;
}
</style>
