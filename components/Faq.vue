<template>
  <div class="container">
    <h1 class="faq-title">
      FAQ
    </h1>
    <div class="columns">
      <!-- Left column begin -->
      <div class="column is-half is-multiline">
        <!--  -->
        <p class="label">
          General
        </p>
        <div v-for="qna in filterQna('General')" :key="`General-${qna.question}`">
          <button @click="toggleBox" class="accordion">
            {{ qna.question }}
          </button>
          <div class="panel">
            <p>{{ qna.answer }}</p>
          </div>
        </div>
        <!--  -->
      </div>
      <!-- Left column end -->
      <!-- Right column begin -->
      <div class="column is-half is-multiline">
        <!-- logistics start -->
        <p class="label">
          Teams &amp; Projects
        </p>
        <div v-for="qna in filterQna('Teams')" :key="`Teams-${qna.question}`">
          <button @click="toggleBox" class="accordion">
            {{ qna.question }}
          </button>
          <div class="panel">
            <p>{{ qna.answer }}</p>
          </div>
        </div>
        <!-- logistics end -->
        <!-- logistics 2 start -->
        <p class="label">
          Logistics
        </p>
        <div v-for="qna in filterQna('Logistics')" :key="`Logistics-${qna.question}`">
          <button @click="toggleBox" class="accordion">
            {{ qna.question }}
          </button>
          <div class="panel">
            <p>{{ qna.answer }}</p>
          </div>
        </div>
        <!-- logistics 2 end -->
      </div>
      <!-- Right column end -->
    </div>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      data: this.prioritizeQuestion()
    }
  },
  methods: {
    toggleBox: (e) => {
      e.target.classList.toggle('active')
      const panel = e.target.nextElementSibling
      if (panel.style.display === 'block') {
        panel.style.display = 'none'
      } else {
        panel.style.display = 'block'
      }
    },
    filterQna(category) {
      return this.data.filter(i => i.category === category)
    },
    prioritizeQuestion() {
      // Have "What is a hackathon?" as the first question
      this.items.forEach((item, index, object) => {
        if (item.question === 'What is a hackathon?') {
          object.splice(index, 1)
          this.items = [item, ...this.items]
        }
      })
      return this.items
    }
  }
}
</script>

<style scoped lang="scss">
@import "bulma/bulma.sass";
.container {
  width: 90%;
  margin: 0 auto;
}
.title {
  text-align: center;
  font-family: "HK Grotesk Regular";
  font-size: 48px;
  color: black;
}
.label {
  font-family: "HK Grotesk Regular";
  color: black;
  font-size: 20px;
}
//Desktop CSS:
.accordion {
  background-color: white;
  color: black;
  cursor: pointer;
  padding: 18px;
  width: 100%;
  margin: 10px auto;
  text-align: left;
  outline: none;
  border: 1.3px solid black;
  border-radius: 5px;
  font-size: 18px;
  font-family: "HK Grotesk Regular";
}
.accordion.active {
  border-bottom: none;
  border-bottom-left-radius: 0px;
  border-bottom-right-radius: 0px;
  margin-bottom: 0px;
}
.panel {
  padding: 18px;
  padding-top: 0;
  background-color: white;
  display: none;
  overflow: hidden;
  border: 1.3px solid black;
  border-top: none;
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  margin: 0 auto;
  margin-bottom: 2%;
  width: 100%;
}
//Mobile CSS:
@include until($desktop) {
}
</style>
