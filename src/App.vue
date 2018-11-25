<template>
  <div id="app">
    <div id="nav" class="js-on">
      <img class="sub-logo" src="./assets/logo.png">
      <router-link to="/"><span>Home</span></router-link>
      <router-link to="/about"><span>About</span></router-link>
      <router-link to="/todo"><span>Todo</span></router-link>
      <div class="nav-toggle"></div>
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
@import "./assets/scss/_common.scss";

#app {
  width: 100%;
  height: 100%;
  display: flex;
  border-top: 10px solid $main_color;
}

#nav {
  position: relative;
  width: $sidebar_size;
  height: 100%;
  padding: 30px;
  background-color: $main_color;
  color: white;
  transition: 0.3s;
  transform: translateX(0);

  @include mq-mb {
    position: absolute;
    transform: translateX(calc(-100% + 10px));
  }

  &:not(.js-on) {
    position: absolute;
    transform: translateX(calc(-100% + 10px));

    .nav-toggle {
      &:after {
        display: block;
      }
    }
  }

  .nav-toggle {
    position: absolute;
    top: 0;
    bottom: 0;
    margin: auto;
    width: 50px;
    height: 50px;
    right: -25px;
    background-color: $main_color;
    border-radius: 50%;

    &:before {
      content: "";
      position: absolute;
      top: 0;
      bottom: 0;
      margin: auto;
      width: 24px;
      height: 2px;
      right: 6px;
      background-color: white;
      transform-origin: 50%;
      transform: rotate(90deg);
    }

    &:after {
      content: "";
      position: absolute;
      top: 0;
      bottom: 0;
      margin: auto;
      width: 24px;
      height: 2px;
      right: 6px;
      background-color: white;
      transform-origin: 50%;
      display: none;
    }
  }

  .sub-logo {
    width: 50px;
    margin: 50px auto;
  }

  a {
    position: relative;
    font-weight: bold;
    color: white;
    display: block;
    margin: 20px 0;

    span {
      position: relative;
      display: inline-block;

      &:before {
        content: "";
        position: absolute;
        right: 0;
        left: 0;
        bottom: -5px;
        margin: auto;
        width: 100%;
        height: 3px;
        background-color: $sub_color;
        transform: scaleX(0);
        transition: 0.3s;
      }
    }

    @include mq-pc {
      &:not(.router-link-exact-active):hover {
        span {
          &:before {
            transform: scaleX(1);
          }
        }
      }
    }

    &.router-link-exact-active {
      cursor: inherit;
      color: $sub_color;
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
  transition: 0.3s;

  @include mq-mb {
    margin: 0 15px;
  }
}
</style>
