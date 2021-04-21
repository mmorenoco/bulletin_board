<template>
  <div class="postit">
    <div
      v-if="postIt.color"
      class="postit-inner"
      :style="{ background: `${postIt.color}` }"
    >
      <p class="close" @click="deletePostit(postIt.id)"></p>
      <h3 class="title">{{ postIt.title }}</h3>
      <p class="note">{{ postIt.message }}</p>
    </div>
    <div v-else class="postit-inner">
      <a class="close" @click="deletePostit(postIt.id)"></a>
      <h3 class="title">{{ postIt.title }}</h3>
      <p class="note">{{ postIt.message }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "PostIt",
  props: {
    postIt: Object,
  },
  methods: {
    deletePostit(id) {
      console.log(id)
      // camelCase Always
      this.$emit('delete-postit', id)
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.postit {
    text-decoration: none;
    color: #000;
    display: block;
    transform: rotate(-6deg);
    text-align: left;
    margin: 15px;
}
.postit-inner {
    height: 10em;
    width: 10em;
    background: #ffc;
    padding: 15px;
    box-shadow: 5px 5px 7px rgba(33, 33, 33, 0.7);
}
.postit:nth-child(even) {
    transform: rotate(4deg);
    position: relative;
    top: 5px;
}
.postit:nth-child(3n) {
    transform: rotate(-3deg);
    position: relative;
    top: -5px;
}
.postit:nth-child(5n) {
    transform: rotate(5deg);
    position: relative;
    top: -10px;
}
.close {
    cursor: pointer;
}
.close:before {
    content: "x";
    position: absolute;
    right: 10px;
    top: 2px;
    font-size: 20px;
}
.note {
    font-family: "Reenie Beanie", arial, sans-serif;
    font-size: 20px;
}
h3 {
    margin-top: 0;
    margin-bottom: 10px;
}
p {
    margin-top: 0;
}
</style>
