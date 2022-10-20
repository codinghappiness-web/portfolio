<template>
  <b-container>
    <b-row
      class="justify-content-center align-items-center"
      style="height: 90vh;"
    >
      <b-col md="4">
        <b-img
          :src="avatar"
          id="avatar-img"
          alt="Omale Happiness Memoji"
          class="img-fluid avatat-img"
        />
      </b-col>

      <b-col md="8">
        <h2 class="intro animate__animated animate__fadeInUp animate__fast">
          Hi 👋,
          <br />I<span>'m Omale Happiness</span>
        </h2>

        <div class="col-md-10 info">
          I have been working as a Data Scientist/Machine Learning Engineer and
          Technical Writer since 2019. I have worked on solving complex problems
          in the fields of engineering and tech.

          <br />
          <b-button
            class="action-btn animate__animated animate__wobble animate__delay-4s animate__fast"
            to="/projects"
          >
            Explore >
          </b-button>

          <b-button class="action-btn" to="/contact" variant="primary">
            Get In Touch
          </b-button>

          <!-- .SOCIAL LINKS SECTION -->
          <div
            class="social-icons animate__animated animate__fadeInUp animate__delay-1s"
          >
            <social-link :to="socialLinks.github">
              <GithubIcon />
            </social-link>

            <social-link :to="socialLinks.linkedin">
              <LinkedinIcon />
            </social-link>

            <social-link :to="socialLinks.twitter">
              <TwitterIcon />
            </social-link>

            <social-link :to="socialLinks.mail">
              <MailIcon />
            </social-link>

            <social-link :to="socialLinks.youtube">
              <YoutubeIcon />
            </social-link>
          </div>
        </div>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import GithubIcon from "vue-ionicons/dist/logo-github.vue";
import LinkedinIcon from "vue-ionicons/dist/logo-linkedin.vue";
import TwitterIcon from "vue-ionicons/dist/logo-twitter.vue";
import YoutubeIcon from "vue-ionicons/dist/logo-youtube.vue";
import MailIcon from "vue-ionicons/dist/md-mail.vue";

export default {
  components: {
    GithubIcon,
    LinkedinIcon,
    TwitterIcon,
    YoutubeIcon,
    MailIcon
  },

  data() {
    return {
      avatar: require("@/assets/avatar.jpeg"),
      // ADD YOUR SOCIAL LINKS HERE 👇
      socialLinks: {
        github: "https://github.com/codinghappiness-web",
        linkedin: "https://www.linkedin.com/in/happiness-omale-3683b71a4",
        twitter: "https://twitter.com/Coding_Happinex",
        mail: "mailto:omalehappiness1@gmail.com",
        youtube: ""
      }
    };
  },

  head: {
    title: "Portfolio ⚡ - Omale Happiness",
    meta: [
      {
        hid: "description",
        name: "description",
        content:
          "Omale Happiness is an awesome front-end developer and technical writer, passionate about building solutions that works across multiple platforms with high accessibility approach. Happiness has vast knowledge in web development with over 3+ years experience in building actual products"
      },
      {
        hid: "og:title",
        name: "og:title",
        content: "Portfolio ⚡ - Omale Happiness"
      },
      {
        property: "og:description",
        content:
          "Omale Happiness is an awesome front-end developer and technical writer, passionate about building solutions that works across multiple platforms with high accessibility approach. Happiness has vast knowledge in web development with over 3+ years experience in building actual products"
      },
      {
        hid: "og:image",
        name: "og:image",
        content: require("@/assets/coding.png")
      }
    ]
  },

  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start();

      setTimeout(() => this.$nuxt.$loading.finish(), 500);
    });
  }
};
</script>
