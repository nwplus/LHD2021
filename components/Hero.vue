<template>
  <div class="hero-container">
    <div class="hero-content">
      <p class="hero-presents-text">
        nwPlus presents
      </p>
      <img :src="lhdLogo" class="hero-lhd-logo">
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
    <img :src="heroBg" class="hero-bg">
  </div>
</template>

<script>
import lhdLogo from '../assets/sprite/svg/hero__logo.svg'
import heroBg from '../assets/sprite/svg/hero__background_bush.svg'
import heroBgMobile from '../assets/sprite/svg/hero__background_mobile.svg'

export default {
  props: {},
  data: function () {
    return {
      lhdLogo,
      heroBg,
      heroBgMobile
    }
  }
}
</script>

<style lang="scss" scoped>
@import "bulma/bulma.sass";

$body-font: "Source Sans Pro", sans-serif;
$hero-background-color: #4A414D;

// Desktop CSS
.hero-container {
  position: relative;
  // Hack for weird white space, TODO: debug
  margin-bottom: -6vw;
}

.hero-content {
  // Make all text white
  color: white;
  // Give breathing room at the top
  padding-top: 5vw;
  position: absolute;
  // Centering an absolute element
  left: 0;
  right: 0;
  margin-left: auto;
  margin-right: auto;
  // Must have specific width
  width: 50%;
  // Centering children
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.hero-bg {
  width: 100%;
  background: $hero-background-color;
}

.hero-presents-text {
  padding-top: 10px;
}

.hero-mailing-list-text {
  font-size: 16px;
  line-height: 20px;
  padding: 10px 0;
}

.hero-lhd-logo {
  width: 146px;
  height: 179px;
}

.hero-email-subscribe {
  display: flex;
  flex-direction: row;
  font-size: 16px;
  line-height: 20px;

  input {
    width: 344px;
    height: 52px;
    color: white;
    background-color: rgba(24, 44, 59, 0.49);
    border: 1px solid rgba(0, 0, 0, 0.08);
    box-sizing: border-box;
    border-radius: 33px;
    padding-left: 20px;
    outline: none;
  }
  ::placeholder {
    color: white;
  }

  button {
    width: 115px;
    height: 52px;
    background: rgba(6, 26, 44, 0.76);
    border: 1px solid rgba(0, 0, 0, 0.08);
    border-radius: 33px;
    margin-left: -115px;
    color: white;
    outline: none;
  }
}

// TODO: add mobile bg for hero

// Mobile CSS
@include until($tablet) {
  .hero-section {
    background-image: url("~@/assets/sprite/svg/hero__background_mobile.svg");
    min-height: 110vh;
    font-size: 12px;
    line-height: 10px;
  }

  .hero-presents-text {
    padding-top: 30px;
  }

  .hero-lhd-logo {
    width: 122.79px;
    height: 160px;
  }

  .hero-mailing-list-text {
    font-size: 14px; 
    padding: 10px 0;
    text-align: center;
  }

  .hero-email-subscribe {
    font-size: 16px;
    line-height: 20px;

    input {
      width: 253px;
      height: 38.24px;
    }

    button {
      width: 78px;
      height: 39px;
      margin-left: -78px;
    }
  }
}
</style>
