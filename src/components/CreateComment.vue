<template>
  <div class="create-comment">
    <div class="form-group">
      <label for>comment</label>
      <input
        type="text"
        class="form-control"
        placeholder="Comment"
        v-model="newComment.body"
      />
    </div>
      <button class="btn btn-warning m-1" @click="addComment()">Add Comment</button>
  </div>
</template>


<script>

// ANCHOR am i pushing new comment to comments or blog.comments
export default {
  name: "create-comment",
  data() {
    return {
      newComment: {}
    };
  },
  mounted() {},
  computed: {
    blog(){
      return this.$store.state.activeBlog
    }
  },
  methods: {
    addComment() {
      this.newComment.blogId = this.blog.blog._id
      this.newComment.creatorEmail = this.blog.blog.creatorEmail
      console.log(this.newComment);
      
      this.$store.dispatch("addComment", this.newComment);
      this.newComment = {};
    }
  },
  components: {}
};
</script>


<style scoped>
</style>