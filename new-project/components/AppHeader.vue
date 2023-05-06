<template lang="pug">
div.header
    nav.header-nav
        a.header-logo(href="#" target="_blank")
            span a
        ul.header-list
            li.list-item
                a.list-link(href="#" target="_blank") about
            li.list-item
                a.list-link(href="#" target="_blank") resume
            li.list-item
                a.list-link(href="#" target="_blank") projects
                div.sublist-wrapper
                    ul.sublist
                        li.sublist-item
                            a.sublist-link(href="#" target="_blank") todo
                        li.sublist-item
                            a.sublist-link(href="#" target="_blank") another project
                        li.sublist-item
                            a.sublist-link(href="#" target="_blank") another project
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
    width: 100%;
    height: 100px;
    background-color: #f0f3f5;
    box-shadow: inset 0px -1px 1px rgba(28, 33, 34, 0.25);

    & .header-nav {
        padding: 15px 40px;
        display: flex;
        justify-content: space-between;
        align-items: center;

        & .header-logo {
            background-color: #0b7a75;
            height: 70px;
            width: 70px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            text-decoration: none;

            &:hover {
                & span {
                    color: #7b2d26;
                }
            }

            & span {
                color: #f0f3f5;
                font-size: 40px;
                transition: color 0.3s ease;
                position: relative;

                &::after {
                    position: absolute;
                    content: '';
                    width: 100%;
                    height: 4px;
                    background-color: #f0f3f5;
                    left: 0px;
                    bottom: 15px;
                }
            }
        }
    }

    & .header-list {
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

            & .list-link,
            & .sublist-link {
                color: #1c2122;
                font-weight: 500;
                transition: color 0.3s ease;
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
                                color: #0b7a75;
                            }
                        }
                    }
                }
            }
        }
    }
}
</style>
