<template>
    <div :class="classes">
        <!-- Main Menu -->
        <wp-menu
            v-else-if="items"
            :items="items"
            class="menu main-menu"
        />
    </div>
</template>

<script>
import WpMenu from "~/components/includes/WpMenu"

export default {
    components: {
        WpMenu
    },
    props: {
        items: {
            type: Array,
            default: ()=> [],
        },
    },
    computed: {
        classes() {
            return [
                "panel-menu",
                { "menu-opened": this.$store.state.menuOpened },
            ]
        },
    },
}
</script>

<style lang="scss" scoped>
.panel-menu {
    position: fixed;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    overflow-y: auto;
    transform: translateY(-100%);
    transition: transform 0.4s $authenticMotion;
    // TODO remove, temporary style for visibility
    background-color: var(--color-orange);

    /deep/ .wp-menu {
        display: inline-block;
        margin: 30px 0 50px;
        padding: 0 0 0 50px;
        list-style: none;
        .nuxt-link,
        a {
            // nuxt-link not working with storybook, targeting a tag
            font-family: var(--font-secondary);
            font-size: 7.7vw;
            font-weight: 700;
            color: var(--color-black);
            text-transform: uppercase;
        }
    }

    // Opened state
    &.menu-opened {
        transform: none;
    }

    // Hovers
    @media #{$has-hover} {
        /deep/ .nuxt-link:hover,
        /deep/ a:hover {
            color: transparent;
            -webkit-text-stroke: 1px var(--color-black);
        }
    }
    // Breakpoints
    @media #{$gt-wide} {
        /deep/ .nuxt-link,
        /deep/ a {
            font-size: 180px;
        }
    }
    @media #{$lt-phone} {
        /deep/.wp-menu {
            padding: 10px 0 0 20px;
        }
    }
}
</style>
