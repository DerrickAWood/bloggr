<template>
  <div class="edit-comment">
    <div class="form-group">
      <label for>comment</label>
      <input
        type="text"
        class="form-control"
        placeholder="Comment"
        v-model="blog.commentData"
      />
    </div>
      <button class="btn btn-warning m-1" @click="editComment()">Edit Comment</button>
  </div>
</template>


<script>


export default {
  name: "edit-comment",
  data() {
    return {
    
    };
  },
  mounted() {},
  computed: {
    blog(){
      return this.$store.state.activeBlog
    }
  },




  methods: {
    editComment() {
      this.$store.dispatch("editComment", this.blog.commentData);
    }
  },
  components: {}
};
</script>


<style scoped>
</style>