<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/newList" >Create a new list</router-link>
  </div>

  <router-view  @new-list="nameslister" :lists = "lists" @listsUpdate="listsUpdate"></router-view>

<!--
 <router-view v-slot="{ Component }"  @new-list="nameslister" :newObj = "newObj? newObj: {}">
  <keep-alive include="Home">
    <component :is="Component" />
  </keep-alive>
</router-view>-->

</template>
<script>
export default {

  data(){
    return{
      lists:[{
      listName:"demo",
      names:["Alexcia","Daja","Shakira","Eleanor","Josefina","Kalli","Adrian","Nallely","Deondre","Elian","Aliya","Britney","Ricky","Annika","Kinsley","Sidney","Oliver","Quinn","Raymond","Jerimiah","Maya","Nathan","Antonio","Simone","Amira","Tara","Gerald","Devon","Brynn","Ruth"],
       unusedNames: ["Shakira","Eleanor","Josefina","Kalli","Adrian","Nallely",]
    },
 
    
    ],
    }
    
  },
  methods:{
    nameslister(obj){
     
      
      
      this.lists.push(obj)
     
    },
    listsUpdate(e){
      this.lists = e;

    },
  },
  beforeMount(){
    if(window.localStorage.getItem("lists")){
      
      this.lists = JSON.parse(window.localStorage.getItem("lists"));
      
    }
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
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}

#nav a.router-link-exact-active {
  color: #00C9A7;
}
</style>
