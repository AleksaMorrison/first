<template lang="pug">
.header
  nav.header-nav
    a.header-logo(href="/")
    ul.header-list
      li.list-item(v-for="link in links" :class="[isActive ? 'active' : '']")
        router-link.list-link(:to="link.path") {{ link.name }}
</template>

<script>
  export default {
    data() {
      return {
        isActive: false,
        links: [
          {
            path: '/resume',
            name: 'resume',
          },
          {
            path: '/playground',
            name: 'playground',
          },
          {
            path: '/contact',
            name: 'contact',
          },
        ],
      };
    },
    computed: {},
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
        width: 50px;
        position: relative;

        &::before {
          content: 'a';
          color: black;
          font-size: 30px;
          transition: color 0.3s ease;
          position: relative;
        }

        &:hover {
          &::before {
            content: 'a';
            color: #ffd166;
            font-size: 30px;
            transition: color 0.3s ease;
            position: relative;
          }
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

            &::before {
              content: '';
              transform: scaleX(1);
              transform-origin: bottom left;
            }
          }
        }

        & .list-link {
          color: #979797;
          font-weight: 500;
          transition: all 0.3s ease;
          text-decoration: none;
          position: relative;

          &::before {
            content: '';
            position: absolute;
            width: 100%;
            transform: scaleX(0);
            height: 2px;
            top: 20px;
            left: 0;
            background-color: #ffd166;
            transform-origin: bottom right;
            transition: transform 0.3s ease-out;
          }
        }
      }
    }
  }
</style>
