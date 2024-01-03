<template>
  <b-container class="page  animate__animated animate__fadeIn">
    <h2>Recent Articles</h2>
    <p>
      Hosted with
      <sub>
        <HeartIcon animate="beat" style="color: red;font-size: 24px;" />
      </sub>
      on Medium &
      <em>
        <a
          href="https://dev.to/codinghappinessweb"
          target="_blank"
          rel="noopener"
          >dev.to</a
        >
      </em>
      <br />
      <br />
      <b-alert
        show
        variant="danger"
        v-if="showErrALert"
        style="display: inline-block;"
      >
        Error loading articles, click
        <a href="https://dev.to/codinghappinessweb" target="_blank">here</a> to
        read 'em instaed.
      </b-alert>
      <b-spinner variant="primary" v-if="showLoader"></b-spinner>
    </p>
    <b-row class="articles" v-if="blogs.length > 0">
      <!-- STATIC ARTICLES -->
      <div
        class="col-md-4"
        v-for="staticArticle in staticArticles"
        :key="staticArticle.articleLink"
      >
        <div>
          <b-card-group deck>
            <b-card
              :img-src="staticArticle.imgLink"
              img-top
              tag="article"
              class="mb-2"
            >
              <h4>{{ staticArticle.title }}</h4>
              <b-badge
                class="animate__animated animate__fadeInUp"
                style="margin: 2px;"
                pill
                :variant="
                  tagVariants[Math.floor(Math.random() * tagVariants.length)]
                "
                >#{{ "Technical Article" }}</b-badge
              >
              <hr />
              <b-card-text>{{ staticArticle.description }}</b-card-text>

              <b-button
                :href="staticArticle.articleLink"
                target="_blank"
                rel="noopener"
                variant="default"
                >Read More..</b-button
              >
            </b-card>
          </b-card-group>
        </div>
      </div>
      <!-- ... -->
      <!-- DEV.TO CONTENT -->
      <div class="col-md-4" v-for="blog in blogs" :key="blog.id">
        <div>
          <b-card-group deck>
            <b-card
              :img-src="blog.image"
              :img-alt="blog.imgAlt"
              img-top
              tag="article"
              class="mb-2"
            >
              <h4>{{ blog.title }}</h4>
              <b-badge
                class="animate__animated animate__fadeInUp"
                style="margin: 2px;"
                v-for="tag in blog.tags"
                :key="tag"
                pill
                :variant="
                  tagVariants[Math.floor(Math.random() * tagVariants.length)]
                "
                >#{{ tag }}</b-badge
              >
              <hr />
              <b-card-text>{{ blog.desc }}</b-card-text>

              <b-button
                :href="blog.url"
                target="_blank"
                rel="noopener"
                variant="default"
                >Read More..</b-button
              >
            </b-card>
          </b-card-group>
        </div>
      </div>
    </b-row>
  </b-container>
</template>
<script>
import HeartIcon from "vue-ionicons/dist/md-heart.vue";
export default {
  components: { HeartIcon },
  data() {
    return {
      showLoader: true,
      showErrALert: false,
      tagVariants: ["primary", "success", "warning", "info", "dark", "danger"],
      blogs: [],
      staticArticles: [
        {
          title:
            "Testing Classification Models for fraud detection using giskard",
          description:
            "This article explains how Giskard open-source ML framework can be used for testing ML models and applied to fraud detection.",
          imgLink:
            "https://assets-global.website-files.com/601d6f7e527cf16fd11a1aae/64afae0c1ece913c9856946d_bank%20auth.webp",
          articleLink: "https://gisk.ar/3JUop6Y"
        },
        {
          title:
            "Building a Heart Disease Prediction model with BentoML and Cleanlab.ai",
          description:
            "In this article, we’ll delve into the fascinating world of building a heart disease prediction model using two powerful tools: BentoML and Cleanlab.ai.",
          imgLink:
            "https://miro.medium.com/v2/resize:fit:1400/format:webp/1*N0pMdcLz0LFVZL8pCH_zvw.jpeg",
          articleLink:
            "https://medium.com/@omalehappiness1/building-a-heart-disease-prediction-model-with-bentoml-and-cleanlab-ai-a95b1c4b7887"
        },
        {
          title: "Bank note authentication in python with streamlit",
          description:
            "The goal of this article is to guide you through the process of building a bank note authentication system step-by-step.",
          imgLink:
            "https://project-assets.showwcase.com/1420x/98746/1683923314584-20230509_183848.jpg?type=webp",
          articleLink:
            "https://www.showwcase.com/show/35057/bank-note-authentication-in-python-with-streamlit"
        },
        {
          title: "Performing face recognition using KNN",
          description:
            "In this article, we will implement a basic form of face recognition using the Haar cascades classifier and k- Nearest Neighbors algorithm.",
          imgLink:
            "https://miro.medium.com/v2/resize:fit:1400/format:webp/1*xy54nBcMgYtKIGsaWkvw7w.png",
          articleLink:
            "https://medium.com/shecodeafrica/performing-face-recognition-using-knn-fe71d87ab619"
        },
        {
          title: "Transforming a horse to a zebra using GAN",
          description:
            "For this article, we will discuss CycleGAN. You can read more about the other different types of GANs here.",
          imgLink:
            "https://miro.medium.com/v2/resize:fit:1400/format:webp/1*OFvz-8TMUZGnIvxb9NEHWA.jpeg",
          articleLink:
            "https://heartbeat.comet.ml/transforming-a-horse-to-a-zebra-using-a-generative-adversarial-network-gan-3124ff27e66c"
        },
        {
          title: "How to do Pivot in Polars",
          description:
            "In this article, we will explore the art of pivoting data using Polars, a blazingly fast dataframe library built on rust, while providing practical code examples to illustrate the process.",
          imgLink:
            "https://project-assets.showwcase.com/1420x/98746/1684249236567-20230516_155858.jpg?type=webp",
          articleLink:
            "https://www.showwcase.com/show/35102/how-to-do-pivot-in-polars"
        },
        {
          title:
            "Polars Explode Multiple Columns Vs Pandas Explode Multiple Columns: A Comparison",
          description:
            "Polars and pandas are popular python libraries for data manipulation and analysis. Both libraries offer an explode() function to break down a column with a list of values into separate rows.",
          imgLink:
            "https://project-assets.showwcase.com/1420x/98746/1683652393140-20230509_180859~2.jpg?type=webp",
          articleLink:
            "https://www.showwcase.com/show/35006/polars-explode-multiple-columns-vs-pandas-explode-multiple-columns-a-comparison"
        },
        {
          title:
            "Data Cleaning and Preprocessing in Pandas and Polars: A Comparison",
          description:
            "In this article, we will discuss the importance of data cleaning and several standard techniques for data cleaning and preprocessing in Python using Pandas and polars.",
          imgLink:
            "https://project-assets.showwcase.com/1420x/98746/1683299656108-1683299646545-WhatsApp%252520Image%2525202023-05-05%2525.jpeg?type=webp",
          articleLink:
            "https://www.showwcase.com/show/34928/data-cleaning-and-preprocessing-in-pandas-and-polars-a-comparison"
        },
        {
          title: "Pandas 2.0 Vs Polars for Data Analysis",
          description:
            "In this article, we will discuss the key differences between Pandas 2.0 and Polars and highlight the benefits of using each library.",
          imgLink:
            "https://project-assets.showwcase.com/1420x/98746/1683202038432-1683202034700-WhatsApp%252520Image%2525202023-05-04%2525.jpeg?type=webp",
          articleLink:
            "https://www.showwcase.com/show/34933/pandas-20-vs-polars-for-data-analysis"
        },
        {
          title:
            "How to use Support Vector Machine (SVM) in Python with scikit-learn in Streamlit",
          description:
            "In this article I will show you how to use SVMs in python using scikit-learn library and integrate this model in streamlit for interactive data exploration.",
          imgLink:
            "https://project-assets.showwcase.com/1420x/98746/1683653183889-20230509_182538.jpg?type=webp",
          articleLink:
            "https://www.showwcase.com/show/34976/how-to-use-support-vector-machine-in-python-with-scikit-learn-in-streamlit"
        },
        {
          title: "Deploying a Text Classification Model in Python",
          description:
            "Using basic NLP principles to build a sentiment analysis model and deploy it with Streamlit",
          imgLink:
            "https://miro.medium.com/max/1400/1*dRfXf70--bxEdfFVbwG5Xw.jpeg",
          articleLink:
            "https://heartbeat.comet.ml/deploying-a-text-classification-model-in-python-e7cd25880364"
        },
        {
          title: "Wine Quality Prediction",
          description:
            "Building a Random Forest Classifier on an imbalanced dataset",
          imgLink:
            "https://miro.medium.com/max/1400/1*1PfuguEzKf6a75LYb2SpFQ.jpeg",
          articleLink:
            "https://heartbeat.comet.ml/wine-quality-prediction-ac10498bec32"
        },
        {
          title: "How I Built a Movie Recommendation System",
          description:
            "A movie recommendation system is an ML-based approach to filtering or predicting the user’s movie preferences...",
          imgLink:
            "https://miro.medium.com/max/1400/1*iU2UuYFubc1AgI86XcWQ2g.jpeg",
          articleLink:
            "https://heartbeat.comet.ml/wine-quality-prediction-ac10498bec32"
        }
      ]
    };
  },
  head: {
    title: "Recent Articles - Omale Happiness",
    meta: [
      {
        hid: "description",
        name: "description",
        content:
          "Read articles written by Omale Happiness, articles include topics under web development (html, css, javascript), mobile app development and many more."
      },
      {
        hid: "og:title",
        name: "og:title",
        content: "Recent Articles - Omale Happiness"
      },
      {
        property: "og:description",
        content:
          "Read articles written by Omale Happiness, articles include topics under web development (html, css, javascript), mobile app development and many more."
      }
    ]
  },
  methods: {
    // get articles hosted on dev.to
    getArticles(username, success, error) {
      let articleImage;
      fetch("https://dev.to/api/articles?username=" + username)
        .then(res => res.json())
        .then(data => {
          data.forEach(article => {
            if (/(hcti.io)/.test(article.image) == true) {
              // use random image from lorem picsum
              articleImage = "https://picsum.photos/600/400";
            } else {
              articleImage = article.social_image;
            }
            this.blogs.push({
              id: article.id,
              title: article.title,
              desc: article.description,
              image: articleImage,
              url: article.url,
              date: article.readable_publish_date,
              tags: article.tag_list,
              imgAlt: article.title + " - Omale Happiness"
            });
          });
          success();
        })
        .catch(err => {
          error();
          console.log("Error fetching articles " + err);
        });
    }
  },
  mounted() {
    this.getArticles(
      "codinghappinessweb",
      () => {
        this.showLoader = false;
      },
      () => {
        this.showErrALert = true;
        this.showLoader = false;
      }
    );
  }
};
</script>
<style scoped>
.container {
  margin-top: 120px;
}
.row {
  margin-top: 40px;
}
.spinner-border {
  margin-top: 40px;
}
.card {
  text-align: left;
  color: #000;
}
</style>
