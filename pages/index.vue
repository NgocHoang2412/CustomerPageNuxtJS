<template>
  <div class="container">
    <div>
       <h1 class="title">
        Welcome to Customer Page
      </h1>
      
      <div class="list-time" v-for="(item, index) in items" :key="item.id">
        <h2 
          >{{item.name}}
        </h2>
        
        <font-awesome-icon :icon="['fas', 'thumbs-up']" v-bind:class="{'icon': item.categoryID==0,  'icon-like': item.categoryID>0}" @click="onclickLike({index})"/>
        
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
    for(let i=0; i<this.items.length; i++){
      this.items[i].categoryID = 0;
    }
},
data () {
    return {
      items: [{
  "_id": {
    "$oid": "5ed857465bdd121d5ceb9d59"
  },
  "name": "Cafe Đá",
  "imageURL": "/cafeden.jpg",
  "defaultPrice": 18000,
  "categoryID": 2,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Cafe đá pha mang nét truyền thống!",
  "createdAt": {
    "$date": "2020-06-04T02:07:02.493Z"
  },
  "updatedAt": {
    "$date": "2020-06-04T02:07:02.493Z"
  }
},{
  "_id": {
    "$oid": "5ee701ea8808511f54533666"
  },
  "name": "Cafe Sữa Đá",
  "imageURL": "/cafesuada.jpg",
  "defaultPrice": 20000,
  "categoryID": 2,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Cafe sữa đá pha chút ngọt ngào!",
  "createdAt": {
    "$date": "2020-06-15T05:06:50.313Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:06:50.313Z"
  }
},{
  "_id": {
    "$oid": "5ee7067e8808511f54533668"
  },
  "name": "Americano",
  "imageURL": "/americano.jpg",
  "defaultPrice": 30000,
  "categoryID": 2,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Americano mang nét hiện đại",
  "createdAt": {
    "$date": "2020-06-15T05:26:22.745Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:26:22.745Z"
  }
},{
  "_id": {
    "$oid": "5ee7075b8808511f54533669"
  },
  "name": "Bạc Sỉu",
  "imageURL": "/bacsiu.jpg",
  "defaultPrice": 20000,
  "categoryID": 2,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Bạc Sỉu đậm đà",
  "createdAt": {
    "$date": "2020-06-15T05:30:03.780Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:30:03.780Z"
  }
},{
  "_id": {
    "$oid": "5ee707a28808511f5453366a"
  },
  "name": "Cappucinno",
  "imageURL": "/cappucinno.jpg",
  "defaultPrice": 40000,
  "categoryID": 2,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Cappucinno",
  "createdAt": {
    "$date": "2020-06-15T05:31:14.665Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:31:14.665Z"
  }
},{
  "_id": {
    "$oid": "5ee707d38808511f5453366b"
  },
  "name": "Caramel Macchiato",
  "imageURL": "/caramelmacchiato.jpg",
  "defaultPrice": 50000,
  "categoryID": 2,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Caramel Macchiato",
  "createdAt": {
    "$date": "2020-06-15T05:32:03.260Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:32:03.260Z"
  }
},{
  "_id": {
    "$oid": "5ee7080f8808511f5453366c"
  },
  "name": "Espresso",
  "imageURL": "/espresso.jpg",
  "defaultPrice": 30000,
  "categoryID": 2,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Espresso",
  "createdAt": {
    "$date": "2020-06-15T05:33:03.646Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:33:03.646Z"
  }
},{
  "_id": {
    "$oid": "5ee708308808511f5453366d"
  },
  "name": "Latte",
  "imageURL": "/latte.jpg",
  "defaultPrice": 40000,
  "categoryID": 2,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Latte",
  "createdAt": {
    "$date": "2020-06-15T05:33:36.738Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:33:36.738Z"
  }
},{
  "_id": {
    "$oid": "5ee708448808511f5453366e"
  },
  "name": "Mocha",
  "imageURL": "/mocha.jpg",
  "defaultPrice": 40000,
  "categoryID": 2,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Mocha",
  "createdAt": {
    "$date": "2020-06-15T05:33:56.190Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:33:56.190Z"
  }
},{
  "_id": {
    "$oid": "5ee708748808511f5453366f"
  },
  "name": "Trà Oolong Hạt Sen",
  "imageURL": "/oolongsen.jpg",
  "defaultPrice": 40000,
  "categoryID": 3,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Trà Oolong Hạt Sen",
  "createdAt": {
    "$date": "2020-06-15T05:34:44.309Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:34:44.309Z"
  }
},{
  "_id": {
    "$oid": "5ee708888808511f54533670"
  },
  "name": "Trà Oolong Vải",
  "imageURL": "/oolongvai.jpg",
  "defaultPrice": 40000,
  "categoryID": 3,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Trà Oolong Vải",
  "createdAt": {
    "$date": "2020-06-15T05:35:04.013Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:35:04.013Z"
  }
},{
  "_id": {
    "$oid": "5ee708ac8808511f54533671"
  },
  "name": "Phúc Bồn Tử",
  "imageURL": "/phucbontu.jpg",
  "defaultPrice": 45000,
  "categoryID": 3,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Phúc Bồn Tử",
  "createdAt": {
    "$date": "2020-06-15T05:35:40.594Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:35:40.594Z"
  }
},{
  "_id": {
    "$oid": "5ee708cb8808511f54533672"
  },
  "name": "Trà Đào Cam Sả",
  "imageURL": "/tradaocamsa.jpg",
  "defaultPrice": 45000,
  "categoryID": 3,
  "unit": "đ",
  "size": {
    "Big": 10000,
    "Medium": 5000
  },
  "description": "Trà Đào Cam Sả",
  "createdAt": {
    "$date": "2020-06-15T05:36:11.748Z"
  },
  "updatedAt": {
    "$date": "2020-06-15T05:36:11.748Z"
  }
}],
    }
  },
// asyncData () {
//     return axios.get('http://localhost:8080/api/items')
//       .then((res) => {
//         return { items: res.data }
//       })
//       .catch((e) => {
//         error({ statusCode: 404, message: 'Not found' })
//       })
//   },
  methods: {
    getItemsLocalStorage(){
      if(process.browser){
        let itemsLocalStorage =  localStorage.getItem("items")
        if(itemsLocalStorage){
          this.items = JSON.parse(itemsLocalStorage)
        }
      }
    },
    onclickLike(index){
      let newValue = 1 - this.items[index.index].categoryID;
      this.items[index.index].categoryID = newValue;
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

.icon {
  color: orange;
  font-size: 30px;
  cursor: pointer;
}

.icon-like {
  color: red;
  font-size: 30px;
  cursor: pointer;
}
</style>
