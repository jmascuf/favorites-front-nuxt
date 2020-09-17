<template>
  <header class="header">
    <nav class="inner">
      <router-link to="/" exact>
        <!-- <img class="logo" src="~/favicon.ico" alt="logo"> -->
        Home
      </router-link>
      <router-link to="/users">Users</router-link>
      <router-link to="/assessments">Assessments</router-link>
      <router-link to="/registries">Registries</router-link>
    </nav>
  </header>
</template>

<style lang="stylus">
.header {
  background-color: #ff6600;
  position: fixed;
  z-index: 999;
  height: 55px;
  top: 0;
  left: 0;
  right: 0;

  .inner {
    max-width: 800px;
    box-sizing: border-box;
    margin: 0px auto;
    padding: 15px 5px;
  }

  a {
    color: rgba(255, 255, 255, 0.8);
    line-height: 24px;
    transition: color 0.15s ease;
    display: inline-block;
    vertical-align: middle;
    font-weight: 300;
    letter-spacing: 0.075em;
    margin-right: 1.8em;

    &:hover {
      color: #fff;
    }

    &.router-link-active {
      color: #fff;
      font-weight: 400;
    }

    &:nth-child(6) {
      margin-right: 0;
    }
  }

  .github {
    color: #fff;
    font-size: 0.9em;
    margin: 0;
    float: right;
  }
}

.logo {
  width: 24px;
  margin-right: 10px;
  display: inline-block;
  vertical-align: middle;
}
</style>