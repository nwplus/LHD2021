<template>
  <div class="intro-section">
    <p class="intro-header-pre">
      Welcome to
    </p>
    <h1 class="intro-header">
      Local Hack Day
    </h1>
    <p class="intro-p1">
      UBC Local Hack Day revolves around <b>inclusivity, diversity, and accessibility</b> — we want you to bring your unique perspectives and experiences to the table!
    </p>
    <p class="intro-p2">
      Over the past 3 years, UBC’s Local Hack Day focused on encouraging beginners and people who are curious about technology to work on a project that focuses on these three main pillars.
    </p>
  </div>
</template>

<script>
</script>

<style lang="scss" scoped>
@import "bulma/bulma.sass";

$body-font: "Source Sans Pro", sans-serif;

// Desktop CSS
.intro-section {
  background-image: url("~@/assets/sprite/svg/intro__background.svg");
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
