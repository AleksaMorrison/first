<template lang="pug">
.playground
  .space
    nav.links
      ul.list-links
        li.list-item
          a.list-link(href="#todo") Todo
        li.list-item
          a.list-link(href="#weather") Weather
        li.list-item
          a.list-link(href="#other2") other2

  #todo.space
    .todo
      ToDo
  #weather.space
    .weather
      Weather
  #other2.space
    .todo
      ToDo
</template>

<script>
  import ToDo from '../components/ToDo';
  import Weather from '../components/Weather';

  definePageMeta({
    layout: 'default',
  });

  export default {
    components: {
      ToDo,
      Weather,
    },
    setup() {},
  };
</script>
<style scoped lang="scss">
  .playground {
    .links {
      display: flex;
      justify-content: center;

      & .list-links {
        display: flex;
        gap: 20px;

        & .list-item {
          &:hover {
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
  }
</style>
