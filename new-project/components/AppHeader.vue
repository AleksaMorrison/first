<template lang="pug">
.header
  nav.header-nav
    a.header-logo(href="/")
      span a
    ul.header-list
      li.list-item
        a.list-link(href="/resume") resume
      li.list-item
        a.list-link(href="/playground") playground
      li.list-item
        a.list-link(href="/contact") contact
</template>

<script>
  export default {
    setup() {},
  };
</script>

<style scoped lang="scss">
  .header {
    z-index: 1000;
    width: 100%;
    height: 80px;
    backdrop-filter: blur(10px);
    position: fixed;
    top: 0;
    box-shadow: inset 0px -1px 1px rgba(28, 33, 34, 0.25);

    & .header-nav {
      padding: 15px 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 20px;

      @media (min-width: 768px) {
        gap: 30px;
      }

      & .header-logo {
        text-decoration: none;
        height: 50px;
        &:hover {
          & span {
            color: #6750a4;
          }
        }

        & span {
          color: black;
          font-size: 30px;
          transition: color 0.3s ease;
          position: relative;
        }
      }
    }

    & .header-list {
      display: flex;
      gap: 10px;

      @media (min-width: 768px) {
        gap: 20px;
      }

      & .list-item {
        &:hover,
        &:active,
        &:focus {
          & .list-link {
            color: black;
          }
        }

        & .list-link {
          color: #979797;
          font-weight: 500;
          transition: color 0.3s ease;
          text-decoration: none;
        }
      }
    }
  }
</style>
