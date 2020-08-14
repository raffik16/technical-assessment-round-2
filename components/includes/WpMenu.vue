<template>
    <ul :class="classes">
        <slot name="before" />

        <wp-menu-item
            v-for="(item, i) in menuItems"
            :key="i"
            class="menu-item"
            :item="item"
            @menu-interacted="menuInteracted"
        />

        <slot name="after" />
    </ul>
</template>

<script>
// Helpers
import _kebabCase from "lodash/kebabCase"
import _upperCase from "lodash/upperCase"
import _get from "lodash/get"
import WpMenuItem from "~/components/includes/WpMenuItem"

export default {
    components: {
        WpMenuItem
    },
    props: {
        location: {
            type: String,
            default: "",
        },
        items: {
            type: Array,
            default: () => [],
        },
    },
    async fetch() {
        // Don't fetch if WordPress menu items provided, use them.
        if (this.items.length) {
            this.menuItems = this.items
            return
        }
    },
    data() {
        return {
            menuItems: this.items,
        }
    },
    computed: {
        classes() {
            return ["wp-menu", `location-${_kebabCase(this.location)}`]
        },
    },
    methods: {
        menuInteracted(event) {
            this.$emit("menu-interacted", event)
        },
    },
}
</script>
