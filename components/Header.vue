<template lang="pug">
  header
    div.inner-margin
      slot

</template>

<style lang="scss" scoped>
  header {
    background-color: transparent;
    box-sizing: border-box;
    padding: 40px 0;

    .inner-margin {
      max-width: 1366px;
      margin: 0 auto;

      a {
        font-size: .9rem;
        margin: 0 15px 0 0;
        line-height: 19px;
        letter-spacing: 1px;
        font-weight: 600;
        text-decoration: none;
        color: #212121;
      }
    }
  }
</style>
