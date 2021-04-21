<template>
  <div id="board">
    <div v-for="postIt in postItList" v-bind:key="postIt.id"  >
      <post-it :postIt="postIt" @delete-postit="delPostIt"/>
    </div>
  </div>
</template>

<script>
import PostIt from "./PostIt.vue";
export default {
  components: { PostIt },
  name: "Board",
  props: ["postItList"],
  methods: {
    delPostIt(id){
      this.$emit('delete', id)
    }
  },
  created () {
    console.log(this.postItList)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#board {
  background-color: #464344;
  border: 10px solid #a5792a;
  height: 100%;
  padding: 25px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
</style>
