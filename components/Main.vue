<template>
  <div id="main-page" v-if="dataReady" style="position: relative; width: 100%;">
    <NavBar id="navbar" :faq="faqFlag" :sponsors="sponsorFlag" />
    <section id="mainSection">
      <div class="mainContent">
        <Hero />
        <Intro id="intro" />
        <Events id="events" :items="events" />
        <About id="about" />
        <FAQ id="faq" v-if="faqFlag" :items="FAQs" />
        <Sponza id="sponza" v-if="sponsorFlag" :items="sponsors" />
      </div>
    </section>
    <Footer />
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import Hero from '@/components/Hero.vue'
import Intro from '@/components/Intro.vue'
import Sponza from '@/components/Sponza.vue'
import Footer from '@/components/Footer.vue'
import fireDb from '@/plugins/firebase.js'
import Events from '@/components/Events.vue'
import About from '@/components/About.vue'
import FAQ from '@/components/faq/Faq.vue'

export default {
  components: {
    NavBar,
    Hero,
    Intro,
    Footer,
    Sponza,
    Events,
    About,
    FAQ
  },
  data() {
    return {
      sponsors: [],
      events: [],
      FAQS: [],
      faqFlag: true,
      sponsorFlag: true,
      dataReady: false
    }
  },
  computed: {
    screenWidth() {
      return screen.width
    }
  },
  async mounted() {
    const Sponsors = 'Sponsors'
    const Events = 'Events'
    const FAQ = 'Faq'
    // data
    const data = await fireDb.getWebsiteData()
    const listOfSponsors = await fireDb.getCollection(Sponsors)
    const listOfEvents = await fireDb.getCollection(Events)
    const FaqQuestions = await fireDb.getCollection(FAQ)

    this.sponsors = listOfSponsors
    this.events = listOfEvents
    this.FAQs = FaqQuestions
    this.faqFlag = FaqQuestions.length !== 0 && data.featureFlags.faqFlag
    this.sponsorFlag = data.featureFlags.sponsorFlag

    this.dataReady = true
  }
}
</script>

<style lang="scss">
@import "bulma/bulma.sass";

@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap");

$body-font: "Source Sans Pro", sans-serif;

#main-page {
  background: linear-gradient(180deg, #4A414C 8.34%, #061A2C 9.19%, #586971 12%, #172C3E 15%, #172C3E 22%, #67757B 26.66%, #B5B5B5 30.2%, #453F4B 34.08%);
  font-family: $body-font;
}

@include until($tablet) {
  #main-page {
    background: linear-gradient(180deg, #4A414C 10%, #061A2C 12%, #586971 14%, #223040 18%, #223040 21%, #67757B 30%, #B5B5B5 30.2%, #453F4B 34.08%);
  }
}
</style>
