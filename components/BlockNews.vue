<template>
    <!-- Nuxt Link for block-text container -->
    <nuxt-link
        :to="to"
        class="block-news"
    >
        <div class="block-text">
            <!-- The Title -->
            <span
                v-if="title"
                class="title"
                v-html="title"
            />
            <!-- The Date -->
            <p
                v-if="date"
                class="date"
                v-html="formattedDate"
            />
        </div>
        <!-- I'd recommend an alt prop if the image istelf doesnt have one. -->
        <!-- The Image -->
        <wp-image
            class="block-image"
            :image="image"
            alt="..."
        />
    </nuxt-link>
    <!-- Close Link Tag -->
</template>

<script>
// Helpers
// TODO changed the function in utils to match designs
import { formatDate } from "@/utils/tools"
import WpImage from "~/components/includes/WpImage"

export default {
    // Add component name
    name: 'block-news',
    components: {
        WpImage
    },
    props: {
        image: {
            type: Object,
            default: () => {},
        },
        title: {
            type: String,
            default: "",
        },
        date: {
            type: String,
            default: "",
        },
        to: {
            type: String,
            default: "",
        },
    },
    computed: {
        formattedDate() {
            // Which format is the date being converted to?
            return formatDate(this.date)
        },
    },
}
</script>

<style lang="scss" scoped>
// Block New UI Should Be Mobile first
.block-news {
    position: relative;
    display: block;
    width: 100%;
    padding-left: 50px;
    box-sizing: border-box;
    
    // Text UI
    .block-text {
        position: absolute;
        top: 50%;
        left: 0;
        transform: translateY(-50%);
        z-index: 40;
        max-width: 400px;
        // I'd love to know more about $authenticMotion
        transition: transform 0.4s $authenticMotion;
    }
    // Title UI
    .title {
        margin: 0;
        font-family: var(--font-secondary);
        font-size: 20px;
        font-weight: 700;

        @media #{$lt-phone} {
            font-size: 15px;
        }
    }
    // Date UI
    .date {
        margin-top: 10px;
        margin-bottom: 0;
        font-size: 14px;

        @media #{$lt-phone} {
            font-size: 12px;
        }
    }
    // Image UI
    .block-image {
        width: 34%;
        transform-origin: left;
        transition: transform 0.4s $authenticMotion;

        @media #{$lt-phone} {
            width: 100%;
        }

        @media #{$lt-tablet} {
            width: 50%;
        }
    }

    // Hovers
    @media #{$has-hover} {
        &:hover {
            z-index: 30;

            .block-image {
                transform: scale(1.4);
            }
            .block-text {
                transform: translate(100px, -50%);
            }
        }
    }
    // Breakpoints
    // Moved breakpoints inside each selector since you'ure using sass.
    // It will make updaing each module easier and with less confliction.
    // Im not sure how @media #{$has-hover}{} is working but you should be able to nest the hovers as well.
}
</style>
