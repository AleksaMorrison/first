<template lang="pug">
div
    h1 Welcome to the homepage
    AppAlert
        | This is an auto-imported component

</template>

<script>
import AppAlert from '../components/AppAlert'

definePageMeta({
    layout: 'default',
})

export default {
    components: {
        AppAlert,
    },
    setup() {},
}
</script>
