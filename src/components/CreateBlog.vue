<template>
  <div class="create-blog">
    <div class="form-group">
      <label for>title</label>
      <input
        type="text"
        class="form-control"
        placeholder="Blog..."
        v-model="newBlog.title"
      />
    </div>
    <div class="form-group">
      <label for>imgUrl</label>
      <input
        type="text"
        class="form-control"
        placeholder="img..."
        v-model="newBlog.imgUrl"
      />
    </div>
    <div class="form-group">
      <label for>name</label>
      <input
        type="text"
        class="form-control"
        placeholder="name..."
        v-model="newBlog.name"
      />
    </div>
    <div class="form-group">
      <label for>body</label>
      <input
        type="text"
        class="form-control"
        placeholder="body..."
        v-model="newBlog.body"
      />
    </div>
    <button type="button" class="btn btn-primary" @click="addBlog()">Add Blog</button>
  </div>
</template>


<script>
export default {
  name: "create-blog",
  data() {
    return {
      newBlog: {}
    };
  },
  mounted() {},
  computed: {},
  methods: {
    addBlog() {
      this.$store.dispatch("addBlog", this.newBlog);
      this.newBlog = {};
    }
  },
  components: {}
};
</script>


<style scoped>
</style>