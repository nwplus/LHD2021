<template>
  <div class="sticky-note">
    <img src="~@/assets/sprite/svg/faq__pin_with_shadow.svg">
    <div class="faq">
      <p class="faq-question">
        {{ faq.question }}
      </p>
      <p class="faq-answer">
        {{ faq.answer }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    faq: {
      type: Object,
      required: true
    }
  },
  methods: {
  }
}
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap");
@import "bulma/bulma.sass";

$body-font: "Source Sans Pro", sans-serif;
$body-color: "#56321E";

//Desktop CSS:
.sticky-note {
    background-image: url("~@/assets/sprite/png/faq__sticky_note.png");
    background-size: 100% 100%;
    background-repeat: no-repeat;
    margin-top: 30px;
}

.faq{
    position: relative;
    z-index: 1;
    margin: auto;
    width: 90%;
    padding-top: 25px;
    padding-bottom: 15px;
    font-family: $body-font;
    color: $body-color;
    font-size: 12px;
    line-height: 15px;
}

.faq-question {
    font-weight: 600;
    padding-bottom: 3px;
    overflow: hidden;
}

.faq-answer {
    font-weight: normal;
    overflow: hidden;
}

img {
    position: static;
    z-index: -1;
    transform: translate(-45%, -25%);
    float:left;
}

//Mobile CSS:
@include until($desktop) {
}
</style>
