<template lang="pug">
span
    menu
    slot
</template>
<script>
import MenuMM from './MenuMM'

export default {
    components: { MenuMM },
    setup() {},

    mounted() {
        console.log(this.count) // 0
    },
}
</script>
