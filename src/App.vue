<template>
  <div id="app">
    <div class="header">
      <img class="logo" alt="Board logo" src="./assets/logo.png" />
      <div class="app-name">Bulletin Board</div>
    </div>
    <div class="column-left">
      <board v-if="showBoard" :postItList="postItList" @delete="deletePostIt"/>
    </div>
    <div class="column-right">
      <post-it-form @createPostit="createPostit"/>
    </div>
  </div>
</template>

<script>
import Board from "./components/Board.vue";
import PostItForm from "./components/PostItForm.vue";
import axios from 'axios'

export default {
  name: "App",
  components: {
    Board,
    PostItForm,
  },
  data() {
    return {
      postItList: [
          {
            id: 1,
            title: 'new title 1',
            message: 'new message',
            color: ''
          },
            {
            id: 15,
            title: 'new title 2',
            message: 'new message',
            color: ''
          },
            {
            id: 20,
            title: 'new title 3',
            message: 'new message',
            color: ''
          }
        ],
        showBoard: true
    }
  },
  methods: {
    deletePostIt(id) {
      // // this.postItList.splice(id--, 1)

      // Funciones mas comunes en editar/crear arrays
      // map / filter / find / reduce

      this.postItList = this.postItList.filter((postit)=> {

        // Si le devolvemos true, ese objeto/number o lo que sea va dentro del arry.
        // Si le devolvemos false, ese elemento no ira en el nuevo array.
        // if(id != postit.id){
        //   return true
        // } else {
        //   return false
        // }
        // if(id != postit.id){
        //   return true
        // } 
        // return false

        return id !== postit.id
        
      })

      // this.postItList = this.postItList.filter((postit)=> id !== postit.id)
  
    },
    createPostit(postit){
      this.postItList.push(postit)
    }
  },
  async created () {

    const res =  await axios.get('https://reqres.in/api/users')

    // post / delete / patch / put
    // Como configurar los encabezados

    // axios.get('https://reqres.in/api/users')
    // .then(()=>{
    // })
    // .catch(err => {
    //   throw err
    // })
    // .finally(()=>{
    // })

    console.log(res.data)




   
    
    console.log('Create APP')
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-wrap: wrap;
  height: 100%;
}
.header {
  width: 100%;
  padding: 15px;
  display: flex;
  align-items: center;
}
.header .logo {
  max-height: 50px;
  border-radius: 5px;
}
.header .app-name {
  margin-left: 25px;
  font-weight: bold;
  font-size: 20px;
}
.column-left {
  width: 80%;
}
.column-right {
  width: 20%;
}
</style>
