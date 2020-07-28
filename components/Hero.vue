<template>
  <div class="hero-section">
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
$hero-background-color: #4A414D;

// Desktop CSS
.hero-section {
  padding-top: 5%;
  background-image: url("~@/assets/sprite/svg/hero__background.svg");
  background-position: 0 0;
  background-repeat: no-repeat;
  background-size: 100vw;
  background-color: $hero-background-color;
  min-height: 130vh;
  position: relative;
  text-align: center;
  color: white;
  font-family: $body-font;
  font-size: 14px;
  line-height: 18px;
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
    border: 1px solid rgba(0, 0, 0, 0.08);
    border-radius: 54px;
    margin-left: -115px;
    color: white;
  }
}

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
  line-height: 10px;
  padding: 10px 0;
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
