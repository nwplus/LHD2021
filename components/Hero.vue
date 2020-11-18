<template>
  <div class="hero-section">
    <img src="../assets/sprite/png/hero__stars.png" class="pulsing" alt="pulsing stars">
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
    <img :src="hackCampLogo" class="hero-lhd-logo">
    <p class="hero-presents-text">
      Powered by <a href="teck.com">Teck Resources</a>. <br>
      Learn. Build. Share.
    </p>
    <!-- MAILING LIST SUBSCRIPTION FORM
    <p class="hero-mailing-list-text">
      Join our mailing list for updates about our events!
    </p>
    <div class="hero-email-subscribe">
      <input v-model="email" type="email" placeholder="Enter email here....">
      <button :class="{active: email}" @click="submit">
        Subscribe
      </button>
    </div> -->
    <p class="hero-mailing-list-text">
      <span class="hero-mailing-list-text bold">
        Registration is now live!</span><br>
      Learn, Build, and Share with us at HackCamp 2020.
    </p>
    <div class="register-btn-container">
      <button @click="register">
        REGISTER HERE
      </button>
    </div>
  </div>
</template>

<script>
import hackCampLogo from '../assets/sprite/svg/hero__logo.svg'
import aboutPost from '../assets/sprite/svg/hero__about_post.svg'
import faqPost from '../assets/sprite/svg/hero__faq_post.svg'
import sponsorsPost from '../assets/sprite/svg/hero__sponsors_post.svg'

export default {
  props: {},
  data: function () {
    return {
      hackCampLogo,
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
  },
  methods: {
    register() {
      window.open(
        'https://forms.gle/LyR1858VvMfhbVFb7',
        '_blank'
      )
    },
    async submit() {
      try {
        await this.$axios.post(process.env.mailingListUrl, {
          email: this.email
        })
        this.email = ''
        this.$toast.success('Successfully added you to our mailing list!', {
          duration: 2500,
          type: 'success',
          position: 'bottom-center'
        })
      } catch (e) {
        const reply = e.response
        if (reply.status === 409) {
          this.$toast.error('You are already subscribed!', {
            duration: 2500,
            position: 'bottom-center',
            type: 'error'
          })
        }
        if (reply.status === 502) {
          this.$toast.error(`An error occured: ${reply.data.errors}`, {
            duration: 2500,
            position: 'bottom-center',
            type: 'error'
          })
        }
        if (reply.status === 400 || reply.status === 500) {
          this.$toast.error(reply.data, {
            duration: 2500,
            position: 'bottom-center',
            type: 'error'
          })
        }
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap");
@import "bulma/bulma.sass";

$body-font: "Source Sans Pro", sans-serif;

// Desktop CSS
.pulsing {
  position: absolute;
  z-index: 1;
  top: 0;
  left: 14vw;
  animation: pulse-black 3s infinite;
  min-width: 60vw;
}

@keyframes pulse-black {
    0% {
        transform: scale(0.99);
        opacity: 0.8;
    }

    50% {
        transform: scale(1);
        opacity: 1;
    }

    100% {
        transform: scale(0.99);
        opacity: 0.8;
    }
}

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
  z-index: 3;
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
  position: relative;
  z-index: 2;
  padding-top: 30px;
  padding-bottom: 10px;
}

.hero-mailing-list-text {
  position: relative;
  z-index: 2;
  font-size: 16px;
  line-height: 20px;
  padding: 10px 0;
  span {
    line-height: 28px;
    font-weight: bold;
  }
}

.hero-lhd-logo {
  position: relative;
  z-index: 2;
  width: 346px;
  height: 136px;
}

.hero-email-subscribe {
  position: relative;
  z-index: 2;
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
    padding-right: 7%;
  }
  ::placeholder {
    color: white;
  }

  button {
    cursor: pointer;
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

.register-btn-container {
  position: relative;
  z-index: 2;
  font-size: 16px;
  line-height: 20px;

  button {
    cursor: pointer;
    height: 52px;
    background: rgba(6, 26, 44, 0.76);
    border: 1px solid rgba(0, 0, 0, 0.08);
    border-radius: 33px;
    color: white;
    outline: none;
    transition: 0.25s;
    font-weight: bold;
    font-size: 18px;
    padding: 0px 36px;
    &:active {
      background: #ffbc96;
      color: #172b3b;
    }
    &:hover {
      background: #ffbc96;
      color: #172b3b;
    }
  }
}

  a {
    color: white;
    text-decoration: underline;
    transition-duration: 0.2s;
  }

  a:hover {
    color: #FFBC96;
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
    width: 300px;
    height: 118px;
  }

  .hero-mailing-list-text {
    font-size: 14px;
    line-height: 10px;
    padding: 10px 0;
  }

  .register-btn-container {
    button{
      font-size: 14px;
    }
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
