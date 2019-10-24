<template>

  <div id="app">
    <div id="nav">
      <!-- <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/test">Test</router-link> -->
    </div>
    <router-view/>
  </div>
</template>




<style>
html {
  height: 1500px;
  background-image: linear-gradient(top, #ffd500,  #ffd500 48%, transparent 48%, transparent 100%);
  /* background: linear-gradient(to bottom, #f8e805 50%, white 50%); */
  margin: 0;
  font-family: 'Open Sans', sans-serif;

}

@import url('https://fonts.googleapis.com/css?family=Jua&display=swap');
@import url('https://fonts.googleapis.com/css?family=Do+Hyeon&display=swap');
@import url('http://fonts.googleapis.com/css?family=Open%20Sans:300,400,500,600,700');


#app {
  font-family: 'Open Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  font-size: 30px;
  color: #020444;
  
}

#nav {
  padding: 30px;
  
}

#nav a {
  font-weight: bold;
  color: #020429;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
