<template>
  <div class="form">
    <div class="form__element">
      <label for="title">
        <span>Title:</span>
      </label>
      <input name="title" type="text" v-model="title" required />
      <!-- <input name="title" type="text" :value="title" @input="setTitle" required /> -->
    </div>

    <div class="form__element">
      <label for="message">
        <span>Message:</span>
      </label>
      <input name="message" type="text" v-model="message" required />
    </div>

    <div class="form__element">
      <label for="custom">
        <span>Custom color:</span>
      </label>
      <input name="custom" type="checkbox" v-model="checked" />
    </div>

    <div class="form__element">
      <label for="color">
        <span>Color:</span>
      </label>
      <input type="color" v-model="color"/>
    </div>
    <div class="form__element">
      <button type="submit" @click="addPostIt">Add</button>
    </div>
  </div>
</template>

<script>
import { uuid } from 'vue-uuid' //Import uuid

export default {
  name: "PostItForm",
  data () {
    return {
      checked: true,
      title: '',
      message: '',
      color: ''
    }
  },
  methods: {
    addPostIt(){
      // if(this.checked){
      //   var colored = this.color
      // }  else {
      //   colored = '#ffc'
      // }
      // let colored
      // if(this.checked){
      //   colored = this.color
      // }  else {
      //   colored = '#ffc'
      // }
      // console.log(colored)
      this.$emit('createPostit', {
        id: uuid.v1(),
        title: this.title,
        message: this.message,
        color: this.checked ? this.color : '#FFC'
      })

    // const objeto = {
    //   key: value,
      
    // }
    this.resetForm()

    },
    resetForm () {
      this.checked = true
      this.title = ' '
      this.message = ' '
      this.color = '#000'
    }
   }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
.form {
  padding: 15px;
}
.form {
  padding: 15px;
}
.form__element {
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
  text-align: left;
}
.form__element label {
  margin-bottom: 10px;
  font-weight: bold;
}
</style>
