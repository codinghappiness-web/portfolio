<template>
  <div class="about page  animate__animated animate__fadeIn">
    <h2>Recent Project</h2>
    <div class="container">
      <div class="row" v-for="(project, index) in projects" :key="index">
        <div class="col-md-5" style="max-height: 300px;overflow: hidden;">
          <img
            :src="project.image_cover"
            :alt="project.title"
            class="project-cover"
          />
        </div>
        <div class="col-md-5">
          <h2 class="mt-3" style="text-align: left;">
            {{ project.title }}
            <hr class="dope" />
          </h2>
          <b-card class="mt-3 mb-3 text-left text-dark">
            <p>{{ project.description }}</p>
            <b-link :href="project.link"
              >Check it out! <LinkIcon style="color: #000;"
            /></b-link>
            <hr />
            <b-link :href="project.github_url"
              >View source code <GithubIcon style="color: #000;"
            /></b-link>
          </b-card>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import LinkIcon from "vue-ionicons/dist/md-link.vue";
import GithubIcon from "vue-ionicons/dist/logo-github.vue";

export default {
  components: {
    GithubIcon,
    LinkIcon
  },
  data() {
    return {
      projects: [
        {
          title: "Loan Prediction App",
          tag: "Datascience, ML",
          description:
            "A loan prediction model based on the DSN Futa and DSC Futa machine learning competitions accepts certain information and attempts to predict whether or not the person will be awarded a loan.",
          image_cover: require("@/assets/loan.jpeg"),
          github_url: "https://github.com/codinghappiness-web/LoanPrediction",
          link:
            "https://codinghappiness-web-loanprediction-loan-prediction-g1w33v.streamlitapp.com/"
        },
        {
          title: "Text Classification App",
          tag: "Datascience, ML",
          description:
            "A state-of-the-art text classification that makes use of the Naive Bayes model to identify if a text's sentiment is positive or negative.",
          image_cover: require("@/assets/sentiment.jpg"),
          github_url:
            "https://github.com/codinghappiness-web/Text-Classify-App",
          link:
            "https://codinghappiness-web-text-classify-app-app-gwgrnp.streamlitapp.com/"
        }
      ]
    };
  },
  methods: {
    isEven(n) {
      if (n % 2 == 0) {
        return true;
      } else {
        return false;
      }
    }
  },
  head: {
    title: "Recent Projects - Omale Happiness",
    meta: [
      {
        hid: "description",
        name: "description",
        content:
          "View all the recents open-sourced projects built with ♥ by Omale Happiness, open-sourced means this project source code are publicly available for everyone to use or modify."
      },
      {
        hid: "og:title",
        name: "og:title",
        content: "Recent Projects - Omale Happiness"
      },
      {
        property: "og:description",
        content:
          "View all the recents open-sourced projects built with ♥ by Omale Happiness, open-sourced means this project source code are publicly available for everyone to use or modify."
      },
      {
        hid: "og:image",
        name: "og:image",
        content: require("@/assets/man-computer.png")
      }
    ]
  }
};
</script>
<style scoped>
.row {
  margin-top: 70px;
}
.project-cover {
  width: inherit;
  border-radius: 3px;
}
hr.dope {
  border: 0;
  width: 90px;
  border-top: 2px solid #dc3545;
  text-align: left;
  margin: initial;
  margin-top: 7px;
  margin-left: 5px;
}
</style>
