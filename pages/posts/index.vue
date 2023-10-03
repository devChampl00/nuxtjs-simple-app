<template>
  <div class="py-4">
    <div class="container">
      <div class="row mb-3">
        <h2 class="fs-3">All Post</h2>
      </div>
      <div class="row mt-3">
        <div class="col-lg-4 mx-0" v-for="(post, i) in articles" :key="i">
          <div class="card mb-2">
            <img :src="post.img" class="card-img-top" :alt="post.title" />
            <div class="card-body">
              <h3 class="card-title fs-5">{{ post.title }}</h3>
              <p class="card-text">
                {{ post.content.substring(0, 175) + "..." }}
                <nuxt-link :to="`/posts/detail/${slug(post.title)}`"
                  >read more</nuxt-link
                >
              </p>
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
  },
};
</script>

<style>
.card-img-top {
  height: 230px;
  object-fit: cover;
}
</style>
