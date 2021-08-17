<template>
  <menu>
    <a class="menu__item">
      <img src="/imgs/home-active.svg" alt="home icon" />
      Home
    </a>
    <a class="menu__item">
      <img src="/imgs/trending.svg" alt="trending icon" />
      Trending
    </a>
    <a class="menu__item">
      <img src="/imgs/subscriptions.svg" alt="subscriptions icon" />
      Subscriptions
    </a>
    <a class="menu__item">
      <img src="/imgs/library.svg" alt="library icon" />
      Library
    </a>
  </menu>
</template>

<style scoped lang="scss">
menu {
  height: 48px;
  margin: 0;
  padding: 0;
  border-top: 1px solid lightgray;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  position: sticky;
  left: 0;
  bottom: 0;
  background-color: white;
  > .menu__item {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    > img {
      width: 24px;
    }
  }
}
</style>
