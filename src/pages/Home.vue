<template>
  <div class="home">
    <h1>Welcome</h1>
    <CreateBlog v-if="$auth.isAuthenticated" />
    <blog v-for="blog in blogs" :blogData="blog" :key="blog._id"></blog>
  </div>
</template>

<script>
import CreateBlog from "../components/CreateBlog";
import Blog from "../components/Blog";
export default {
  name: "home",
  data(){
    return{}
  },
  mounted(){
    console.log(this.$auth)
    this.$store.dispatch("getBlogs")
  },
  computed: {
    blogs(){
      return this.$store.state.blogs
    },
    created(){
      this.$store.dispatch("getBlogs")
    }
  },
  methods: {},
  components: { CreateBlog , Blog}
};
</script>
