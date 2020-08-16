<template>
  <div class="about-container">
    <div class="about-content">
      <img :src="aboutPlank" class="about-header">
      <p class="about-p1">
        Last year, Learn and Build Day events were held months apart.
        This year, we plan on running the event as a virtual conference weekend,
        with a focus on learning and workshops on the first day, and building and hacking on the second day.
      </p>
      <p class="about-p2">
        This year, due to the COVID-19 pandemic, we will be holding our event in a virtual format.
        As the health and safety of our attendees is our top priority, we will continue to keep an eye on the current
        situation within BC and provide updates through our website and social media channels should anything change.
      </p>
    </div>
    <img :src="aboutBg" class="about-bg">
  </div>
</template>

<script>
import aboutBg from '../assets/sprite/svg/about__background.svg'
import aboutBgMobile from '../assets/sprite/svg/about__background_m.svg'
import aboutPlank from '../assets/sprite/svg/about__welcome_plank.svg'

export default {
  props: {},
  data: function () {
    return {
      aboutBg,
      aboutBgMobile,
      aboutPlank
    }
  }
}
</script>

<style lang="scss" scoped>
@import "bulma/bulma.sass";

$body-font: "Source Sans Pro", sans-serif;

// Desktop CSS
.about-container {
  display: flex;
  justify-content: center;
  position: relative;
}

.about-content {
  position: absolute;
  padding-top: 30%;
}

.about-bg {
  width: 100%;
  background: #577079;
}

.about-p1, .about-p2 {
  text-align: center;
}

.about-header {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 80%;
}

.about-p1, .about-p2 {
  // Spacing
  margin: 1em auto 0 auto;
  max-width: 60ch;
  // Text
  font-family: $body-font;
  font-size: 1.5rem;
  color: white;
}

// Mobile CSS
@include until($desktop) {
  .about-p1, .about-p2 {
    font-size: 1rem;
  }
}

@include until($tablet) {
  .about-content {
    padding-top: 20%;
  }
  .about-header {
    width: 60%;
  }
  .about-p1, .about-p2 {
    font-size: 0.7rem;
  }
}

@include until(350px) {
  .about-p1, .about-p2 {
    font-size: 0.5rem;
  }
}
</style>
