<template>
  <div class="container">
    <div>
       <h1 class="title">
        Welcome to Customer Page
      </h1>
      <div class="list-time" v-for="item in items" :key="item.id">
        <h2 
          >{{item.name }}
        </h2>
        <font-awesome-icon :icon="['fas', 'thumbs-up']" @click="onclickLike"/>
      </div>
     
      <h2 class="subtitle">
        My riveting Nuxt.js project
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import axios from 'axios'

export default {

created() {
    this.getItemsLocalStorage();
},
data () {
    return {
      items: {}
    }
  },
asyncData () {
    return axios.get('http://localhost:8080/api/items')
      .then((res) => {
        return { items: res.data }
      })
      .catch((e) => {
        error({ statusCode: 404, message: 'Not found' })
      })
  },

  methods: {
    getItemsLocalStorage(){
      if(process.browser){
        let itemsLocalStorage =  localStorage.getItem("items")
        if(itemsLocalStorage){
          this.items = JSON.parse(itemsLocalStorage)
        }
      }
    },
    onclickLike(){
      console.log("click like here")
    }
  },
   components: {
    Logo
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.list-time {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  height: 50px;
  width: 100%;
  padding-left: 200px;
  padding-right: 200px;
  background-color: powderblue;
}
</style>
