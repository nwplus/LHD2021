<template>
  <div class="about-section">
    <h1 class="about-header">
      We're trying something new!
    </h1>
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
</template>

<script>
</script>

<style lang="scss" scoped>
@import "bulma/bulma.sass";

// Desktop CSS
.about-header, .about-p1, .about-p2 {
  text-align: center;
}

.about-header {
  font-size: 30px;
  color: #56321E;
}

.about-p1, .about-p2 {
  // Spacing
  margin: 1em auto;
  max-width: $tablet;

  // Text
  font-family: "Source Sans Pro", sans-serif;
  font-size: 24px;
  /*color: white;*/
}

// Mobile CSS
@include until($tablet) {
  .about-p1, .about-p2, .about-header {
    margin: 1em;
    text-align: center;
  }
}
</style>
