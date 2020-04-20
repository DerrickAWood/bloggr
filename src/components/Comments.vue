<template>
  <div class="comments col-3">
    <h5>{{commentData.body}}</h5>
    <button class="btn btn-danger" v-show="this.$auth.userInfo.email == commentData.creatorEmail" @click="deleteComment(commentData.id)">Delete</button>
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
  computed: {},
  methods: {
    async deleteComment(id) {
    await this.$store.dispatch("deleteComment", id)
     this.$store.dispatch("getBlog", this.commentData.blogId)
    }
    },
  components: {}
};
</script>


<style scoped>
</style>