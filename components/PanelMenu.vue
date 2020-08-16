<template>
    <div :class="classes">
        <!-- I understand this menu component is dynamicly established, it's missing some syntax sugar.  -->
        <!-- It would better explain where the data is coming from and what it's going to look like on the front end. -->
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
            // Something like this would help better understand the returned object for the menu.
            // Expected result example:
            // {
            //  "wp-menu-name" : "Directors"
            // },
            // {
            //  "wp-menu-name" : "Work"
            // }
            // {
            //  "wp-menu-name" : "About"
            // },
            // {
            //  "wp-menu-name" : "News"
            // },
            // {
            //  "wp-menu-name" : "Contact"
            // }
            type: Array,
            default: ()=> [],
        },
    },
    computed: {
        classes() {
            return [
                // Toggleing menu open classes
                "panel-menu",
                { "menu-opened": this.$store.state.menuOpened },
            ]
        },
    },
}
</script>

<style lang="scss" scoped>
// A few browsers may cause overflow issues if you don't define right:0 and bottom:0
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
        // Consider using Flexbox
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

    // You should be able to nest the hovers within the respected selector.
    // Hovers
    @media #{$has-hover} {
        /deep/ .nuxt-link:hover,
        /deep/ a:hover {
            color: transparent;
            -webkit-text-stroke: 1px var(--color-black);
        }
    }
    // You should be able to nest breakpoints within the respected selector.
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
