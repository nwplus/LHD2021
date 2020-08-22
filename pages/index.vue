<template>
  <div id="main-page" style="position: relative; width: 100%;">
    <NavBar id="navbar" :faq="faqFlag" />
    <section id="mainSection">
      <div class="mainContent">
        <Hero />
        <Intro id="intro" :intro="intro" :volunteerOpen="volunteerFlag" :mentorOpen="mentorFlag" />
        <Events id="events" :items="events" />
        <About id="about" />
        <FAQ id="faq" v-if="faqFlag" :items="FAQs" />
        <Sponza id="sponza" v-if="sponsorFlag" :items="sponsors" />
      </div>
    </section>
    <Footer :text="footer" />
  </div>
</template>

<script>
import NavBar from '~/components/NavBar.vue'
import Hero from '~/components/Hero.vue'
import Intro from '~/components/Intro.vue'
import Sponza from '~/components/Sponza.vue'
import Footer from '~/components/Footer.vue'
import fireDb from '~/plugins/firebase.js'
import Events from '~/components/Events.vue'
import About from '~/components/About.vue'
import FAQ from '~/components/faq/Faq.vue'

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
  computed: {
    screenWidth() {
      return screen.width
    }
  },
  asyncData: async () => {
    const Sponsors = 'Sponsors'
    const Events = 'Events'
    const FAQ = 'Faq'
    // functions
    // data
    const data = await fireDb.getWebsiteData()
    const listOfSponsors = await fireDb.getCollection(Sponsors)
    const listOfEvents = await fireDb.getCollection(Events)
    const FaqQuestions = await fireDb.getCollection(FAQ)

    return {
      info: data.WelcomeText,
      sponsors: listOfSponsors,
      outro: data.OutroText,
      footer: data.FooterText,
      events: listOfEvents,
      intro: {
        text: data.IntroText,
        introButtonEnabled: data.IntroButtonEnabled,
        introLink: data.IntroButtonLink,
        signUpText: data.SignUpText
      },
      FAQs: FaqQuestions,
      faqFlag: FaqQuestions.length !== 0 && data.faqFlag,
      ...data.featureFlags
    }
  }
}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap");

$body-font: "Source Sans Pro", sans-serif;

#main-page {
  background: linear-gradient(180deg, #4A414C 8.34%, #061A2C 9.19%, #586971 14.68%, #3A3946 16.43%, #042539 20.49%, #67757B 26.66%, #B5B5B5 30.2%, #453F4B 34.08%);
  font-family: $body-font;
}
</style>
