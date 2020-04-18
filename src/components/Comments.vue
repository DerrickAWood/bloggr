<template>
  <div class="comments col-3">
    <h5>{{commentData.body}}</h5>
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
    },
  components: {}
};
</script>


<style scoped>
</style>