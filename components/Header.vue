<template>
  <header :class="{ '--hidden': isHidden }">
    <Nav />
    <Tags />
  </header>
</template>

<script>
const _debounce = require('lodash.debounce')

export default {
  data() {
    return {
      prevScrollPosition: 0,
      isHidden: false,
    }
  },
  mounted() {
    window.addEventListener('scroll', _debounce(this.onScroll, 100))
  },
  destroyed() {
    window.removeEventListener('scroll', _debounce(this.onScroll, 100))
  },
  methods: {
    onScroll(event) {
      const scrollPosition = window.pageYOffset
      if (scrollPosition > this.prevScrollPosition) {
        this.isHidden = true
      } else {
        this.isHidden = false
      }
      this.prevScrollPosition = scrollPosition
    },
  },
}
</script>

<style scoped lang="scss">
header {
  background-color: white;
  z-index: 999;
  position: sticky;
  top: 0;
  left: 0;
  transition: transform 0.1s linear;
  &.--hidden {
    transform: translateY(-100%);
  }
}
</style>
