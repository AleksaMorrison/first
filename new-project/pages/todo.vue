<template lang="pug">
.container
    .section
        ToDo
    
</template>

<script>
import ToDo from '../components/ToDo'

definePageMeta({
    layout: 'default',
})

export default {
    components: {
        ToDo,
    },
    setup() {},
}
</script>
<style scoped lang="scss">
.container {
    margin-top: 100px;
    padding: 20px 16px;
    height: 100%;
    width: 100%;

    @media (min-width: 768px) {
        padding: 80px 120px;
    }

    & .section {
        width: 100%;
    }
}
</style>
