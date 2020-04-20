<template>
  <div class="comment col-3">
    <h5>{{commentData.body}}</h5>
    <button class="btn btn-danger" v-show="this.$auth.userInfo.email == commentData.creatorEmail" @click="deleteComment(commentData.id)">Delete</button>
    <button class="btn btn-warning m-1" @click="editComment()">Edit Comment</button>
    <div v-show="this.$auth.userInfo.email == commentData.creatorEmail" class="form-group">
      <label for>comment</label>
      <input
        type="text"
        class="form-control"
        placeholder="Comment"
        v-model="commentData.body"
      />
    </div>
  </div>
</template>


<script>


export default {
  name: "comment",
  props: ["commentData"],
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
    async deleteComment(id) {
    await this.$store.dispatch("deleteComment", id)
     this.$store.dispatch("getBlog", this.commentData.blogId)
    },
    editComment() {
      this.$store.dispatch("editComment", this.commentData);
    }
    },
  components: { }
};
</script>


<style scoped>
</style>