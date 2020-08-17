<template>
  <a :href="formatURL(item.url)" class="link" target="_blank" rel="noopener noreferrer">
    <img
      :class="{[item.rank]: true}"
      :src="item.imgURL"
      :alt="item.name"
    >
  </a>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  methods: {
    formatURL(url) {
      if (!url.includes('http')) {
        return `http://${url}`
      } else {
        return url
      }
    }
  }
}
</script>

<style scoped lang="scss">
  @import "bulma/bulma.sass";

  img {
    display: block;
    transition-duration: 0.2s;
  }

  img:hover {
    transform: scale(1.08);
  }

  .tera {
    max-width: 900px;
    max-height: 260px;
  }

  .giga {
    max-width: 700px;
    max-height: 240px;
  }

  .mega {
    max-width: 600px;
    max-height: 220px;
  }

  .kilo {
    max-width: 500px;
    max-height: 200px;
  }

  .in-kind {
    max-width: 300px;
    max-height: 150px;
  }

  //Mobile CSS:
  @include until($desktop) {
    img {
      display: inline;
      max-width: 200px !important;
    }
  }
</style>
