<template>
  <div id="app">
    <div id="nav">
      <img class="sub-logo" src="./assets/logo.png">
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
@import "./assets/scss/_variables.scss";
@import "./assets/scss/_mixin.scss";
@import "./assets/scss/_base.scss";
@import "./assets/scss/_animation.scss";

#app {
  width: 100%;
  height: 100%;
  display: flex;
  border-top: 10px solid $main_color;
}

#nav {
  width: $sidebar_size;
  height: 100%;
  padding: 30px;
  background-color: $main_color;
  color: white;
  transition: 0.3s;
  transform: translateX(0);

  @include mq-mb {
    position: absolute;
    transform: translateX(-150%);
  }

  .sub-logo {
    width: 50px;
    margin: 50px auto;
  }

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
  position: relative;
  margin: 0 30px;

  @include mq-mb {
    margin: 0 15px;
  }
}
</style>
