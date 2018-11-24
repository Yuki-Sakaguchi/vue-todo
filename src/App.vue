<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
    <div id="contents">
      <transition name="router-transition">
        <router-view/>
      </transition>
    </div>
  </div>
</template>


<style lang="scss">
$main_color: #203143;
$sidebar_size: 300px;

* {
  box-sizing: border-box;
}

html,
body,
#app {
  width: 100%;
  height: 100%;
}

body {
  border-top: 10px solid $main_color;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
}

#nav {
  width: $sidebar_size;
  height: 100%;
  padding: 30px;
  background-color: $main_color;
  color: white;

  a {
    font-weight: bold;
    color: white;
    display: block;
    margin: 15px 0;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

#contents {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.router-transition-enter-active {
  transition: all .3s ease .3s;
}
.router-transition-leave-active {
  position: absolute;
  transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.router-transition-enter,
.router-transition-leave-to {
  transform: translateX(10px);
  opacity: 0;
}
</style>
