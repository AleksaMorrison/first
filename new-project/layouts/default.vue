<template lang="pug">
div
  AppHeader
  .body
    slot
</template>

<script>
  import AppHeader from '../components/AppHeader';
  export default {
    components: {
      AppHeader,
    },
    setup() {},
  };
</script>
<style lang="scss" scoped>
  .body {
    margin-top: 160px;
  }
</style>
