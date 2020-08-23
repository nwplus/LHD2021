<template>
  <div class="hero-section">
    <div class="wooden-post">
      <a v-scroll-to="'#intro'" href="#">
        <img :src="aboutPost" alt="about">
      </a>
      <a v-scroll-to="'#faq'" href="#">
        <img :src="faqPost" alt="faq">
      </a>
      <a v-scroll-to="'#sponza'" href="#">
        <img :src="sponsorsPost" alt="sponsors">
      </a>
    </div>
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
      <input v-model="email" type="email" placeholder="Enter email here....">
      <button :class="{active: email}">
        Subscribe
      </button>
    </div>
  </div>
</template>

<script>
import lhdLogo from '../assets/sprite/svg/hero__logo.svg'
import aboutPost from '../assets/sprite/svg/hero__about_post.svg'
import faqPost from '../assets/sprite/svg/hero__faq_post.svg'
import sponsorsPost from '../assets/sprite/svg/hero__sponsors_post.svg'
export default {
  props: {},
  data: function () {
    return {
      lhdLogo,
      aboutPost,
      faqPost,
      sponsorsPost,
      email: null
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
  background-image: url("~@/assets/sprite/png/hero__background.png");
  background-position: 0 0;
  background-repeat: no-repeat;
  background-size: 100vw;
  min-height: 81vw;
  position: relative;
  text-align: center;
  color: white;
  font-family: $body-font;
  font-size: 14px;
  line-height: 18px;
  overflow-x: hidden;
}

.wooden-post {
  display: flex;
  flex-direction: column;
  position: absolute;
  top: 25vw;
  left: 8vw;
  width: 17vw;
  img:hover {
    transition: 0.25s;
    &:hover {
      transform: scale(1.05);
    }
  }
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
    margin-left: -118px;
    color: white;
    outline: none;
    transition: 0.25s;
    &.active {
      background: #ffbc96;
      color: #172b3b;
    }
  }
}

// Mobile CSS
@include until($tablet) {
  .hero-section {
    background-image: url("~@/assets/sprite/png/hero__background_mobile.png");
    min-height: 165vw;
    font-size: 12px;
    line-height: 10px;
  }

  .wooden-post {
    display: none;
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
