<template>
  <div class="container">
    <div id="bulletin-title-container">
      <img id="bulletin-title" src="~@/assets/sprite/svg/faq__section_title.svg" alt="faq-bulletin-title">
    </div>
    <div id="bulletin-board-container">
      <img id="bulletin-board" src="~@/assets/sprite/png/faq__bulletin_board.png" alt="faq-bulletin-board">
      <div class="columns faqs">
        <div class="column is-one-quarter">
          <div v-for="faq in items" :key="`Common-${faq.question}`">
            <FaqNote :faq="faq" />
          </div>
        </div>
        <div class="column is-one-quarter">
          <div v-for="faq in items" :key="`Common-${faq.question}`">
            <FaqNote :faq="faq" />
          </div>
        </div>
        <div class="column is-one-quarter">
          <div v-for="faq in items" :key="`Common-${faq.question}`">
            <FaqNote :faq="faq" />
          </div>
        </div>
        <div class="column is-one-quarter">
          <div v-for="faq in items" :key="`Common-${faq.question}`">
            <FaqNote :faq="faq" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FaqNote from '~/components/faq/FaqNote.vue'

export default {
  components: {
    FaqNote
  },
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      leftFaqs: this.getFaqColumn(true),
      rightFaqs: this.getFaqColumn(false)
    }
  },
  methods: {
    getFaqColumn(left) {
      const isLeft = (e, i) => left ? i % 2 === 0 : i % 2 !== 0
      return this.items.filter(isLeft)
    },
    // For future usage
    filterFaq: (category) => {
      return this.items.filter(i => i.category === category)
    }
  }
}
</script>

<style scoped lang="scss">
@import "bulma/bulma.sass";
//Desktop CSS:
.container {
  position: relative;
  width: 100%;
}

#bulletin-board-container {
  position: relative;
}

#bulletin-board {
  position: static;
  z-index: -1;
  min-height: 100vh;
}

.faqs {
  position: static;
  z-index: 10;
  width: 80%;
  margin: 0 auto;
}

#bulletin-title-container {
  background-image: url("~@/assets/sprite/svg/faq__wooden_plank.svg");
  background-position: 0 0;
  background-repeat: no-repeat;
  position: static;
  z-index: 1;
  height: 10vh;
}

#bulletin-title {
  background-image: url("~@/assets/sprite/svg/faq__section_title.svg");
  background-position: 0 0;
  background-repeat: no-repeat;
  text-align: center;
}

.label {
  font-family: "HK Grotesk Regular";
  color: black;
  font-size: 20px;
}

//Mobile CSS:
@include until($desktop) {
}
</style>
