<template lang="pug">
div.header
    nav.header-nav
        a.header-logo(href="/")
            span a
        ul.header-list
            li.list-item
                a.list-link(href="/resume" target="_blank") resume
            li.list-item
                a.list-link playground
            li.list-item
                a.list-link(href="#" target="_blank") contact me

</template>

<script>
export default {
    setup() {},
}
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
        gap: 30px;

        & .header-logo {
            text-decoration: none;
            height: 50px;
            &:hover {
                & span {
                    color: #7b2d26;
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
        gap: 20px;

        & .list-item {
            opacity: 0.5;
            transition: opacity 0.3s ease;
            &:hover {
                & .list-link {
                    color: black;
                    opacity: 1;
                }

                & > .sublist-wrapper {
                    display: block;
                }
            }

            & .list-link,
            & .sublist-link {
                color: black;
                opacity: 0.5;
                font-weight: 500;
                transition: opacity 0.3s ease;
                text-decoration: none;
            }

            &:nth-child(3) {
                position: relative;
            }

            & > .sublist-wrapper {
                display: none;
                position: absolute;
                width: 140px;
                padding: 20px;
                background-color: transparent;

                & .sublist {
                    display: flex;
                    flex-direction: column;
                    background-color: white;
                    border-radius: 8px;
                    gap: 15px;
                    box-shadow: 0px 2px 5px rgba(28, 33, 34, 0.25);
                    padding: 15px;
                    top: 40px;

                    & .sublist-item {
                        &:hover {
                            & .sublist-link {
                                opacity: 1;
                            }
                        }
                    }
                }
            }
        }
    }
}
</style>
