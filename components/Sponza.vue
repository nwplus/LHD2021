<template>
  <div class="sponza">
    <div id="sponsorList">
      <div class="sponsorCategory">
        <div v-for="item in listOfTera" :key="item.name" class="sponsorWrapper">
          <SponsorImage :item="item" />
        </div>
      </div>
      <div class="sponsorCategory">
        <div v-for="item in listOfGiga" :key="item.name" class="sponsorWrapper">
          <SponsorImage :item="item" />
        </div>
      </div>
      <div class="sponsorCategory">
        <div v-for="item in listOfMega" :key="item.name" class="sponsorWrapper">
          <SponsorImage :item="item" />
        </div>
      </div>
      <div class="sponsorCategory">
        <div v-for="item in listOfKilo" :key="item.name" class="sponsorWrapper">
          <SponsorImage :item="item" />
        </div>
      </div>
      <div class="sponsorCategory">
        <div v-for="item in listOfInKind" :key="item.name" class="sponsorWrapper">
          <SponsorImage :item="item" />
        </div>
      </div>
    </div>
    <img :src="sponsorSash" class="sponsor-sash" alt="Our Sponsors">
    <BecomeSponsorButton />
  </div>
</template>

<script>
import sponsorSash from '../assets/sprite/svg/sponsor__backgound.svg'
import SponsorImage from '~/components/SponsorImage'
import BecomeSponsorButton from '~/components/becomeSponsorButton'

export default {
  components: { SponsorImage, BecomeSponsorButton },
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  data: function () {
    return {
      sponsorSash
    }
  },
  computed: {
    listOfTera: function () {
      return this.items.filter(item => item.rank === 'tera')
    },
    listOfGiga: function () {
      return this.items.filter(item => item.rank === 'giga')
    },
    listOfMega: function () {
      return this.items.filter(item => item.rank === 'mega')
    },
    listOfKilo: function () {
      return this.items.filter(item => item.rank === 'kilo')
    },
    listOfInKind: function () {
      return this.items.filter(item => item.rank === 'in-kind')
    }
  }
}
</script>

<style scoped lang="scss">
@import "bulma/bulma.sass";

//Desktop CSS:
.sponsorCategory {
  margin-bottom: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.sponsorWrapper {
  margin: 30px;
}

.sponza {
  position: relative;
  margin-top: 2%;
  text-align: center;
}

.sponsor-sash {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 100%;
}

#sponsorList {
  padding-top: 35%;
  position: absolute;
  // Centering an absolute element
  left: 0;
  right: 0;
  margin-left: auto;
  margin-right: auto;
  // Must have specific width
  width: 60%;
}

//Mobile CSS:
@include until($tablet) {
  .sponsorCategory {
    flex-direction: column;
  }
  .sponsorWrapper {
    max-width: 300px;
    margin: 15px;
  }
}
</style>
