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
    <comments v-for="comment in comments" :commentData="comment" :key="comment._id"></comments>
    <create-comment></create-comment>
    <edit-Blog></edit-Blog>
      </div>
    </div>
  </div>
</template>


<script>
import EditBlog from "../components/EditBlog"
import CreateComment from "../components/CreateComment"
import Comments from "../components/Comments"
export default {
  name: "blog-details",
  data() {
    return {
    };
  },
  created() {
    this.$store.dispatch("getBlog", this.$route.params.blogId);
    this.$store.dispatch("getBlog", this.blogData._id)
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
  components: { Comments, CreateComment, EditBlog }
};
</script>