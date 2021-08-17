<template>
  <div class="home">
    <Header />
    <main>
      <Videos />
    </main>
    <Menu />
  </div>
</template>

<style lang="scss">
* {
  box-sizing: border-box;
}

html {
  font-size: 10px;
  font-family: Roboto, Arial, sans-serif;
}

body {
  margin: 0;
  padding: 0;
}

img {
  max-height: 100%;
}

.custom-button {
  border: none;
  background: transparent;
}

.home {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>
