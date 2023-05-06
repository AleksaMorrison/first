<template lang="pug">
div.footer
    nav.footer-nav
            ul.footer-list
                li.list-item
                    a.list-link(href="#" target="_blank") main
                li.list-item
                    a.list-link(href="#" target="_blank") resume
                li.list-item
                    a.list-link(href="#" target="_blank") contact me
    
</template>

<script>
export default {
    setup() {},
}
</script>

<style scoped lang="scss">
.footer {
    width: 100%;
    height: 100px;
    background-color: #f0f3f5;
    position: fixed;
    left: 0;
    bottom: 0;

    & .footer-nav {
        padding: 15px 40px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: max-content;
        margin: 0 auto;
    }

    & .footer-list {
        display: flex;
        gap: 20px;

        & .list-item {
            &:hover {
                & .list-link {
                    color: #0b7a75;
                }

                & > .sublist-wrapper {
                    display: block;
                }
            }

            & .list-link {
                color: #1c2122;
                font-weight: 500;
                transition: color 0.3s ease;
                text-decoration: none;
            }
        }
    }
}
</style>
