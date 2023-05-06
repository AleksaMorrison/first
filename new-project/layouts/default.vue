<template lang="pug">
div
    AppHeader
    slot
</template>

<script>
import AppHeader from '../components/AppHeader'
export default {
    components: {
        AppHeader,
    },
    setup() {},
}
</script>
