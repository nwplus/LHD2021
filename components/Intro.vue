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
$hero-background-color: #4A414D;

// Desktop CSS
.intro-container {
  display: flex;
  justify-content: center;
  position: relative;
}

.intro-content {
  position: absolute;
  padding-top: 20%;
}

.intro-bg {
  width: 100%;
  background: linear-gradient(180deg, #48414E, 5%, #243745, #566770, #072639);
}

.intro-header, .intro-p1, .intro-p2 {
  text-align: center;
}
.intro-header {
  font-size: 30px;
  color: #56321E;
}

.intro-header-pre {
  font-size: 12px;
  color: #56321E;
  text-align: center;
}

.intro-p1, .intro-p2 {
  // Spacing
  margin: 1em auto;
  max-width: $tablet;
  // Text
  font-family: $body-font;
  font-size: 24px;
  color: white;
}
// Mobile CSS
@include until($tablet) {
  .intro-background {
    background-image: url("~@/assets/sprite/svg/intro__background_m.svg");
  }
  .intro-p1, .intro-p2, .intro-header {
    margin: 1em;
    text-align: center;
  }
}
</style>
