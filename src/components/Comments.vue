<template>
  <div class="comments col-3">
    comments go here
    <p>{{commentsData}}</p>
  </div>
</template>


<script>
export default {
  name: "comments",
  props: ["commentsData"],
  data() {
    return {
    };
  },
  mounted() {},
  computed: {},
  methods: {
    },
  components: {}
};
</script>


<style scoped>
</style>