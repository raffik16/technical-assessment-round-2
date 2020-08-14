<template lang="html">
  <section>
    <block-news
      :image="API.pages[0].featuredImage"
      :title="API.pages[0].title"
      :data="API.pages[0].date"
      :to="API.pages[0].uri"
    />

    <featured-block
      :imagePrimary="API.pages[0].featuredImage"
      :imageSecondary="API.pages[1].featuredImage"
      :title="API.pages[0].title"
      :credit="API.pages[3].title"
      :to="API.pages[0].uri"
    />

    <panel-menu :items="API.menuItems" />
  </section>
</template>

<script>
import DB from "/db.json";

// Components
import BlockNews from "~/components/BlockNews";
import FeaturedBlock from "~/components/Featured";
import PanelMenu from "~/components/PanelMenu";

export default {
  components: {
    FeaturedBlock,
    BlockNews,
    PanelMenu
  },
  data() {
    return {
      API: DB
    };
  }
};
</script>
