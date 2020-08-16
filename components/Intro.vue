<template>
  <div class="intro-container">
    <div class="intro-content">
      <img :src="introPlank" class="intro-header">
      <p class="intro-p1">
        UBC Local Hack Day revolves around <b>inclusivity, diversity, and accessibility</b> — we want you to bring your unique perspectives and experiences to the table!
      </p>
      <p class="intro-p2">
        Over the past 3 years, UBC’s Local Hack Day focused on encouraging beginners and people who are curious about technology to work on a project that focuses on these three main pillars.
      </p>
    </div>
    <img :src="introBg" class="intro-bg">
  </div>
</template>

<script>
import introBg from '../assets/sprite/svg/intro__background.svg'
import introBgMobile from '../assets/sprite/svg/intro__background_m.svg'
import introPlank from '../assets/sprite/svg/intro__welcome_plank.svg'

export default {
  props: {},
  data: function () {
    return {
      introBg,
      introBgMobile,
      introPlank
    }
  }
}
</script>

<style lang="scss" scoped>
@import "bulma/bulma.sass";

$body-font: "Source Sans Pro", sans-serif;

// Desktop CSS
.intro-container {
  position: relative;
  // Hack for weird white space, TODO: debug
  margin-bottom: -10px;
}

.intro-content {
  padding-top: 20%;
  position: absolute;
  // Centering an absolute element
  left: 0;
  right: 0;
  margin-left: auto;
  margin-right: auto;
  // Must have specific width
  width: 50%;
}
.intro-bg {
  width: 100%;
  padding-bottom: 5%;
  background: linear-gradient(180deg, #48414E, 5%, #243745, #566770, 65%, #072639);

}

.intro-header {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 80%;
}

.intro-p1, .intro-p2 {
  // Spacing
  max-width: $tablet;
  margin: 1em auto 0 auto;
  // Text
  text-align: center;
  font-family: $body-font;
  font-size: 1.5rem;
  color: white;
}

// Mobile CSS
@include until($desktop) {
  .intro-p1, .intro-p2 {
    font-size: 1rem;
  }
}

@include until($tablet) {
  .intro-p1, .intro-p2 {
    font-size: 0.7rem;
  }
}

@include until(350px) {
  .intro-p1, .intro-p2 {
    font-size: 0.5rem;
  }
}
</style>
