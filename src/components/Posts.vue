<template>
  <div class="container-fluid mt-4">
    <h1 class="h1">Posts</h1>
    <div class="posts">
      <div class="post" v-for="post in posts" :key="post.id">
        <h3>{{ post.title }}</h3>
        <p>{{ post.body }}</p>
        <hr>
      </div>
    </div>
  </div>
</template>
<script>
import api from '@/api'
export default {
  data () {
    return {
      loading: false,
      posts: [],
      model: {}
    }
  },
  async created () {
    this.refreshPosts()
  },
  methods: {
    async refreshPosts () {
      this.loading = true
      this.posts = await api.getPosts()
      this.loading = false
    }
  }
}
</script>