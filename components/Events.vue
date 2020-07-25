<template>
  <div class="mainContainer">
    <div class="no-overflow rows is-3-tablet">
      <div v-for="item in sortedEvents" :key="item.order" :class="{ flipped: isFlipped(item) }">
        <div class="events row">
          <div class="image-container">
            <img :src="getImageURL(item)" class="image">
          </div>
          <p class="valuesText">
            {{ item.text }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import orderBy from 'lodash.orderby'
export default {
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  computed: {
    sortedEvents: function () {
      return orderBy(this.items, 'order')
    }
  },
  methods: {
    isFlipped(item) {
      return item?.title === 'Build Day'
    },
    getImageURL(item) {
      return require(`@/assets/sprite/svg/events__${item.key}.svg`)
    }
  }
}
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap");
@import "bulma/bulma.sass";
$gap: 6%;
$mobile: 415px;
$dark-brown: #56321e;
$brown: #817067;
$dark-blue: #06273a;
$white: #ffffff;
$heading-font: "Caveat Brush";
$body-font: "Source Sans Pro", sans-serif;

.mainContainer {
  background-image: url("~@/assets/sprite/svg/events__background.svg");
  background-position: 0 0;
  background-repeat: no-repeat;
  background-size: 100vw;
  min-height: 133vw;
  position: relative;
  &::before {
    background: linear-gradient(180deg, $dark-blue 0%, $white 100%);
    display: block;
    content: "";
    position: absolute;
    height: 100%;
    width: 100%;
    z-index: -1;
  }
  @include until($tablet) {
    background-image: url("~@/assets/sprite/svg/events__background_sm.svg");
    min-height: 237vw;
  }
}

.rows {
  padding: 12% $gap;
  .row {
    .valuesText {
      width: 50vw;
      color: $white;
      font-family: $body-font;
      font-style: normal;
      font-weight: normal;
      font-size: 24px;
      line-height: 30px;
      @include until($tablet) {
        font-size: 18px;
        line-height: 24px;
      }
      @include until($mobile) {
        font-size: 12px;
        line-height: 15px;
      }
    }
    img {
      @include until($tablet) {
        width: 40vw;
      }
    }
  }
  .flipped {
    .row {
      bottom: 30%;
      position: absolute;
      right: $gap;
    }
  }
}
</style>
