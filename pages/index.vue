<template lang="pug">
  div
    section.first
      Carousel

</template>

<script>
import Carousel from "~/components/Carousel"

export default {
  components: {
    Carousel
  }
}
</script>

<style lang="scss">
section {
  position: relative;
  background-color: #fafafa;
  height: 100vh;

  &.first {
    height: calc(100vh - 100px);
  }
}

::-webkit-scrollbar {
  width: 4px;
}

::-webkit-scrollbar-thumb {
  background: #212121;
}
</style>
