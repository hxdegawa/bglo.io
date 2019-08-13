<template lang="pug">
  .article-card
    slot
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.article-card {
  position: relative;
  display: inline-block;
  overflow: hidden;
  vertical-align: top;

  box-shadow: 0px 0px 8px #cecece;
  border-radius: 5px;

  width: calc(100% / 4 - 20px);
  margin-bottom: 30px;
  padding-bottom: 20px;

  &:nth-of-type(4n + 1) {
    margin-right: 10px;
  }

  &:nth-of-type(4n + 2), &:nth-of-type(4n + 3) {
    margin: 0 15px 0 15px;
  }

  &:nth-of-type(4n + 4) {
    margin-left: 10px;
  }

  img {
    width: 100%;
    height: 240px;
    object-fit: cover;
  }

  h3 {
    position: relative;
    max-width: calc(100% - 40px);
    padding: 15px 0;
    margin: 0 auto;
    font-size: .9rem;
    letter-spacing: 1px;
    font-weight: 600;
    text-decoration: none;
    color: #333333;
  }

  p {
    @extend h3;
    padding: 0 0 20px 0;
    font-size: .8rem;
    font-weight: 400;
    line-height: 18px;
    color: #555;
  }

  .date, .tags > .tag {
    display: inline-block;
    font-size: .7rem;
    vertical-align: top;
    font-weight: 400;
    line-height: 18px;
  }

  .date {
    float: left;
    margin-left: 20px;
    padding: 3px 0;
    color: #808080;
  }

  .tags {
    float: right;
    margin-right: 20px;

    .tag {
      margin-right: 10px;
      padding: 2px 6px;
      border: solid 1px #000000;
      text-transform: capitalize;
      border-radius: 3px;
      transition: 0.2s ease;

      &:hover {
        background-color: #212121;
        color: #fafafa;
      }

      &:last-of-type {
        margin-right: 0px;
      }
    }
  }

  &:after {
    content: "";
    clear: both;
    display: table;
  }
}
</style>
