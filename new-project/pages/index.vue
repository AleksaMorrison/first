<template lang="pug">
.space
  .intro
    h1 Hi, I am Aleksandra.
</template>

<script>
  definePageMeta({
    layout: 'default',
  });

  export default {
    components: {},
    setup() {},
  };
</script>

<style scoped lang="scss">
  .space {
    & .intro {
      display: flex;
      justify-content: center;
    }
  }
</style>
