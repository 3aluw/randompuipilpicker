<template>

  <div class="lists-container">
<div class="saved-list" v-for="(list, index) in lists" :key="list.listName" @click="listExtrcat(index)"> 
 {{list.listName}}
 <ul class="list-item-hover">
  reamaining : {{list.unusedNames.length }}/ {{list.names.length}}
  <li v-for="name in list.unusedNames">{{name}}</li></ul>
</div></div>
<button @click="studentSelector">Pick someone</button>

<h1 class="picked">{{pickedP}}</h1>
<h2>reamaining students : {{currentObj.unusedNames.length}}</h2>
<button @click="saver">Save Lists </button>
<button  @click="deleter" :class="{ danger : deleteMode }">Delete a list</button>
<button @click="reseter">Reset default</button>
</template>

<script>



export default {
  name: 'Home',
  props:{
    lists : Object,
  },
   emits: ["listsUpdate","new-list"],

  data(){
    return{
     
      currentObj:{
      listName:null,
      names:null,
      unusedNames: null,
    },
      pickedP: null,
      currentObjIndex : 0,
      deleteMode : false,
      listsToDelete : [], 
    
    
    }
  },

  beforeMount() {

   if(this.currentObj.listName === null){ 
    this.currentObj.listName = this.lists[0].listName;
this.currentObj.unusedNames = this.lists[0].unusedNames;
this.currentObj.names = this.lists[0].names;
this.currentObjIndex = 0;
   }; 
   
  }, 
  unmounted(){
    this.lists.splice(this.currentObjIndex ,1,this.currentObj);
    this.$emit("listsUpdate", this.lists)
  },
  
  
  methods:{
    listExtrcat(index){
      console.log(event)
     if(!this.deleteMode){
this.currentObj.listName = this.lists[index].listName;
this.currentObj.unusedNames = this.lists[index].unusedNames;
this.currentObj.names = this.lists[index].names;
this.currentObjIndex = index;
     }
     else{
      !this.listsToDelete.includes(index) ? this.listsToDelete.push(index): this.listsToDelete.splice(this.listsToDelete.indexOf(index) < 0 ? this.listsToDelete.length : this.listsToDelete.indexOf(index) ,1);
     }
},
 studentSelector(){



  let pickedN = Math.floor(Math.random()*this.currentObj.unusedNames.length);
  this.pickedP = this.currentObj.unusedNames[pickedN]
  this.currentObj.unusedNames.splice(pickedN,1);


    if( this.currentObj.unusedNames.length === 0){
      
      this.currentObj.unusedNames = [...this.currentObj.names];
     
      
    }

},
deleter(){
this.deleteMode = true;

},
saver(){
  this.lists.splice(this.currentObjIndex ,1,this.currentObj);
  let listsString = JSON.stringify(this.lists);
  localStorage.setItem("lists",listsString);
  
},
reseter(){
  console.log(this.lists[0])
 
 localStorage.removeItem("lists");
 document.location.reload();
}
},


}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
      height: 2rem;
}
button{
  background: #B39CD0;
  border: 2px solid #B39CD0;
  color: black;
  font-size: 1rem;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
  border-radius: 3px;
  margin: 1rem;
  padding: .5rem;
  cursor: pointer;
  min-width: 10vw;
  min-height: 3vh;
}
button:hover{
  background: none;
  color: black;
}
input{
  min-width: 50vw;
  min-height: 10vh;
  font-size: 3rem;
  text-align: center;
}
.lists-container{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

.saved-list{
  position: relative;
  margin: 0.5rem;
 min-height: 8rem;
 min-width:10rem ;
  border: 1px solid black;
  padding: 10px;
    display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;  
  color: #845EC2;
  font-size: 3rem;
}
.list-item-hover{
  padding: 0.5rem;
  border-radius: 5px;
 display: none;
  position: absolute;
  bottom: -60%;
  right: -40%;
  text-align: center;
  border: 1px solid black;
  list-style: none;
  font-size: 1rem;
  color: black;
  background-color: rgb(248, 248, 66);
  opacity: 0.8;
}
.saved-list:hover > .list-item-hover{
  display: block;
}
.danger{
  background-color: red;
  color: white;
  border: none;
}
</style>
