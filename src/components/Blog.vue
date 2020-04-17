<template>
  <div v-if="$auth.isAuthenticated" class="blog col-3">
    user: {{blogData.creatorEmail}}
    <h3> {{blogData.title}}</h3>
    <button class="btn btn-warning" @click="viewBlog()">View Blog</button>
  </div>
</template>


<script>
export default {
  name: "blog",
  props: ["blogData"],
  data() {
    return {
    };
  },
  mounted() {},
  computed: {},
  methods: {
    viewBlog(){
      this.$store.commit("setActiveBlog", {})
      this.$router.push({
        name: "BlogDetails",
        params: {blogId: this.blogData._id}
      })
    }
    },
  components: {}
};
</script>


<style scoped>
</style>