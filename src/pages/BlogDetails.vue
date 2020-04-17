<template>
  <div class="blog-details container-fluid">
    <div class="row">
      <div class="col-12 text-center">
        <h5>{{blog.title}}</h5>
        <img class="img-fluid" :src="blog.imgUrl" />
        <p>{{blog.body}}</p>
        <p>{{blog.creatorEmail}}</p>
        <button class="btn btn-dark m-1" @click="$router.push({name:'home'})">Back</button>
        <button class="btn btn-danger" @click="deleteBlog()">Delete</button>
        <button class="btn btn-warning m-1" v-show="this.$auth.userInfo.email == blog.creatorEmail" @click="editBlog()">Edit</button>
    <comments v-for="comment in comments" :commentData="comment" :key="comment._id"></comments>
      </div>
    </div>
  </div>
</template>


<script>
import Comments from "../components/Comments"
export default {
  name: "blog-details",
  data() {
    return {};
  },
  created() {
    this.$store.dispatch("getBlog", this.$route.params.blogId);
  },
  computed: {
    blog() {
      console.log(this.$store.state.activeBlog);
      
      return this.$store.state.activeBlog.blog;
    },
    comments(){
      return this.$store.state.activeBlog.comments
    }
  },
  methods: {
    deleteBlog() {
      this.$router.push({ name: "Blogs" });
      this.$store.dispatch("deleteBlog", this.blog._id);
    }
  },
  components: { Comments }
};
</script>