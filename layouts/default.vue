<template lang="pug">
  div
    Header
      nuxt-link(to="about") About
      nuxt-link(to="works") Works
      nuxt-link(to="history") History
      nuxt-link(to="blog") Blog
    nuxt
</template>

<script>
import Header from "~/components/Header"

export default {
  components: {
    Header
  }
}
</script>


<style lang="scss">
  @import url('https://rsms.me/inter/inter.css');

  html {
    font-family: 'Inter', 'Noto Sans JP', sans-serif;
    cursor: url("~assets/cursor.svg") 2 2, url("~assets/cursor.png") 2 2, auto;

    a, button {
      cursor: url("~assets/pointer.svg") 4 4, url("~assets/pointer.png") 4 4, pointer !important;
    }
  }

  @supports (font-variation-settings: normal) {
    html { font-family: 'Inter var', 'Noto Sans JP', sans-serif; }
  }

  a {
    color: #212121;
    letter-spacing: 1px;
    font-weight: 600;
    margin: 0px 2px;
  }

  body {
    margin: 0;
    background-color: #ffffff;
    color: #212121;

    * {
      box-sizing: border-box;
    }

    main {
      max-width: 1366px;
      padding-top: 40px;
      margin: 0 auto;
    }
  }
</style>
