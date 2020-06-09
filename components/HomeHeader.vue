<template>
  <nav class="header-bar">
    <div class="container">
      <div class="left-header">
        <nuxt-link to="/">home</nuxt-link>
      </div>
      <div class="right-header">
        <div class="input-wrapper">
          <input type="text" placeholder="find what you need" />
        </div>
        <div class="right-nav">
          <nuxt-link to="/">
            <img class="icons" src="http://bisnis.cls-indo.co.id/assets/images/shopping-cart.svg" />
          </nuxt-link>
          <nuxt-link to="/">
            <img class="icons" src="http://bisnis.cls-indo.co.id/assets/images/globe.svg" />
          </nuxt-link>
          <nuxt-link to="/">
            <img class="icons" src="http://bisnis.cls-indo.co.id/assets/images/inbox2.svg" />
          </nuxt-link>
          <nuxt-link to="/">
            <img class="icons" src="http://bisnis.cls-indo.co.id/assets/images/account2.svg" />
          </nuxt-link>
        </div>
      </div>
    </div>
  </nav>
</template>
<style>
.header-bar {
  background-color: var(--main-bg-color);
  height: 60px;
  overflow: hidden;
  display: flex;
  justify-content: flex-end;
  color: white;
}
.header-bar .container {
  display: flex;
  max-width: calc(960px + (100% - 960px) / 2);
  justify-content: flex-end;
  padding: 0px 15px;
  margin: 0px auto;
  width: calc(960px + (100% - 960px) / 2);
}
.header-bar .container > div {
  height: 60px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
.header-bar .left-header {
  width: 250px;
}
.header-bar .container > .right-header {
  width: calc(100% - 250px);
  flex-direction: row;
  justify-content: space-between;
}
.header-bar a {
  color: white;
  text-decoration: none;
}
.header-bar .right-header .right-nav {
  float: right;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header-bar .right-header .right-nav a{
  height: 32px;
  width: 46px;
  display: flex;
  justify-content: center;
}
.header-bar .right-header .right-nav img.icons {
  width: 32px;
  height: auto;
  padding: 5px;
}
.header-bar input {
  margin: 0px 5px 0px;
}
.button {
  border-radius: 5px;
}
</style>
