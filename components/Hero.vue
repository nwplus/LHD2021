<template>
  <div class="hero-section">
    <p class="hero-presents-text">
      nwPlus presents
    </p>
    <span class="hero-lhd-logo" />
    <img :src="lhdLogo">
    <p class="hero-presents-text">
      Learn. Build. Share.
    </p>
    <p class="hero-mailing-list-text">
      Join our mailing list for updates about our events!
    </p>
    <div class="hero-email-subscribe">
      <input type="email" placeholder="Enter email here....">
      <button>Subscribe</button>
    </div>
  </div>
</template>

<script>
import lhdLogo from '../assets/sprite/svg/hero__logo.svg'
export default {
  props: {
  },
  data: function () {
    return {
      lhdLogo: lhdLogo
    }
  },
  mounted: function () {
    setTimeout(() => {
      this.isTimeout = true
    }, 300)
  }
}
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap");
@import "bulma/bulma.sass";

$body-font: "Source Sans Pro", sans-serif;

// Desktop CSS
.hero-section {
  padding-top: 5%;

  background-image: url("~@/assets/sprite/svg/hero__background.svg");
  background-position: 0 0;
  background-repeat: no-repeat;
  background-size: 100vw;
  min-height: 120vh;
  position: relative;
  text-align: center;
  color: white;
  font-family: $body-font;
  font-size: 14px;
  line-height: 18px;
}

.hero-mailing-list-text {
  font-size: 16px;
  line-height: 20px;
}

.hero-lhd-logo {
  background-image: url("~@/assets/sprite/svg/hero__logo.svg");
  width: 146px;
  height: 179px;
  position: relative;
}

.hero-email-subscribe {
  font-size: 16px;
  line-height: 20px;

  input {
    width: 344px;
    height: 52px;
    background-color: rgba(24, 44, 59, 0.49);
    border: 1px solid rgba(0, 0, 0, 0.08);
    box-sizing: border-box;
    border-radius: 33px;
    padding-left: 20px;

  }
  ::placeholder {
    color: white;
  }

  button {
    width: 115px;
    height: 50px;
    background: rgba(6, 26, 44, 0.76);
    border-radius: 54px;
    margin-left: -115px;
    color: white;
  }
}

// Mobile CSS
@include until($tablet) {
  .about-background {
    background-image: url("~@/assets/sprite/svg/hero__background.svg");
  }
}
</style>
