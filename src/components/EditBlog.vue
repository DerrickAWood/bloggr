<template>
  <div v-show="this.$auth.userInfo.email == blog.creatorEmail"  class="Edit-Blog">
    <div class="form-group">
      <label for>title</label>
      <input
        type="text"
        class="form-control"
        placeholder="Blog..."
        v-model="changedBlog.title"
      />
    </div>
    <div class="form-group">
      <label for>imgUrl</label>
      <input
        type="text"
        class="form-control"
        placeholder="img..."
        v-model="changedBlog.imgUrl"
      />
    </div>
    <div class="form-group">
      <label for>body</label>
      <input
        type="text"
        class="form-control"
        placeholder="body..."
        v-model="changedBlog.body"
      />
    </div>
    <button class="btn btn-warning m-1" @click="editBlog()">Edit</button>
  </div>
</template>


<script>
export default {
  name: "Edit-Blog",
  data() {
    return {
      changedBlog: {}
    };
  },
  mounted() {},
  computed: {
    blog() {
      console.log(this.$store.state.activeBlog);
      
      return this.$store.state.activeBlog.blog;
    }
  },
  methods: {
    editBlog() {
      this.changedBlog.id = this.blogId
      this.changedBlog.creatorEmail = this.blog.creatorEmail
      this.$store.dispatch("editBlog", this.changedBlog);
      this.changedBlog = {};
    }
  },
  components: {}
};
</script>


<style scoped>
</style>