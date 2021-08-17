<template>
  <nav>
    <a href="/">
      <img class="logo" src="/imgs/logo.svg" alt="logo" />
    </a>
    <div class="nav-right">
      <button class="custom-button">
        <img class="icon-search" src="/imgs/search.svg" alt="search" />
      </button>
      <button class="custom-button">
        <img class="icon-avatar" src="/imgs/avatar.jpg" alt="user avatar" />
      </button>
    </div>
  </nav>
</template>

<style scoped lang="scss">
nav {
  height: 48px;
  display: flex;
  align-items: center;
  box-shadow: 0 0 3px 1px lightgray;
  padding: 0 12px;
  button {
    height: 48px;
    width: 48px;
  }
  .logo {
    width: 89px;
    vertical-align: middle;
  }
  .nav-right {
    display: flex;
    flex-direction: row;
    margin-left: auto;
  }
}
</style>
