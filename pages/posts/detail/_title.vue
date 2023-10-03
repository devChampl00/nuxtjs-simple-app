<template>
  <div class="py-4">
    <div class="container">
      <div class="row justify-content-center mt-3">
        <div class="col-lg-6">
          <article>
            <!-- Post header-->
            <header class="mb-4">
              <!-- Post title-->
              <h1 class="fw-semibold fs-3 mb-1">{{ post.title }}</h1>
            </header>
            <!-- Preview image figure-->
            <figure class="mb-4">
              <img
                class="img-fluid rounded"
                :src="post.img"
                :alt="post.title"
              />
            </figure>
            <!-- Post content-->
            <section class="mb-5">
              {{ post.content }}
            </section>
          </article>

          <div class="action mt-4">
            <div
              class="btn btn-outline-secondary btn-sm px-3 mb-3"
              @click="$router.go(-1)"
            >
              Back
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import articles from "@/pages/posts/articles.json";

export default {
  layout(_) {
    return "custom";
  },

  data() {
    return {
      articles: articles,

      post: this.findPost(this.$route.params.title),
    };
  },

  methods: {
    slug(str) {
      if (str.includes(" ")) {
        str = str.replaceAll(" ", "-");
      }
      return str
        .split("")
        .map((x) => x.toLowerCase())
        .join("");
    },

    findPost(title) {
      return articles.find((x) => this.slug(x.title) === title);
    },
  },
};
</script>

<style>
.card-img-top {
  height: 230px;
  object-fit: cover;
}
</style>
